# The Journey Begins - Mobile Weather Dashboard
![Pack your umbrella!](../images/weather_wizard.webp)

Welcome to the first step of your Grafana Cloud adventure! In this chapter, you'll be setting up a weather forecast dashboard that you can check any time to keep an eye on the skies. Think of this as your magical artifact—only instead of conjuring storms, you'll be predicting them. Here's how your weather forecast will look when it's done. The dashboard is optimized for viewing on mobile devices so you can check the forecast on your phone.

![Screenshot of the default forecast panel for New York City](../images/grafana_cloud_nyc_weather_panel.png)

This is a fun and interactive journey where you’ll:

1. Sign up for Grafana Cloud.
2. Enable the Infinity plugin and data source.
3. Import a pre-configured weather dashboard.
4. Use the National Weather Service API to pull in your local weather forecast.
5. Customize your dashboard to make it uniquely yours.

Grab your gear, and let's begin!

## System Requirements 📃

- [Grafana Cloud Account](https://grafana.com/auth/sign-up/create-user)
- A modern browser (Chrome, Firefox, Edge, or Safari)
- A [National Weather Service API](https://www.weather.gov/documentation/services-web-api) Gridpoint URL (we’ll help you find it!)

## Step 1: Sign up for Grafana Cloud ☁️

Your first task is to sign up for a free Grafana Cloud account.

1. Head over to [Grafana Cloud](https://grafana.com/auth/sign-up/create-user).
2. Choose one of the identity providers to create your account.

![Screenshot of the Grafana Cloud signup page](../images/grafana_cloud_signup.png)

3. Verify that you are not a robot.

![Screenshot of the Grafana Cloud bot checker](../images/grafana_cloud_bot_check.png)

4. Give your stack a name and choose a region.

![Screenshot of the Grafana Cloud stack creation page](../images/grafana_cloud_stack_region.png)

5. Wait a few minutes while your stack provisions. Now would be a good time to get up an stretch or get yourself a warm beverage ☕.
6. Congratulations, you have your own Grafana Cloud stack! You can log on and manage your account settings and stacks at grafana.com. 

> **🪄 Protip:**
> 
> Bookmark your stack's URL for quick and easy reference later. Your stack URL looks like this: https://YOURSTACKNAME.grafana.net

## Step 2: Enable the Infinity Plugin and Data Source ♾️

Next, you’ll enable a plugin that will help us pull in weather data from the US National Weather Service API.

1. In your Grafana Cloud stack, click on the **Connections >> Add New Connection** menu option on the left sidebar.

![Screenshot of the add new connection button](../images/grafana_cloud_add_new_connection.png)

2. Search for **Infinity** and click on the Infinity data source.

![Screenshot of the Infinity plugin](../images/grafana_cloud_search_for_infinity.png)

3. Click on the **Install** button to install the Infinity data source.

![Screenshot of the Install button](../images/grafana_cloud_install_button.png)

4. It may take a couple of minutes for the Infinity data source to become visible. Click on the **Connections >> Data sources** link on the left menu. 

![Screenshot of Grafana Cloud data sources](../images/grafana_cloud_data_sources.png)

5. Click on "Add new data source"

![Screenshot of the Add new data source link](../images/grafana_cloud_add_new_datasource.png)

6. Search for "Infinity". If it doesn't show up wait a minute and refresh the page. Once you see it click on it to add the Infinity data source.

![Screenshot of the Infinity data source](../images/grafana_cloud_add_new_datasource_2.png)

7. You'll see a popup notification once the data source has been correctly added. 

![Screenshot of the popup notification for adding a data source successfully](../images/grafana_cloud_datasource_added.png)

8. Leave the default name `yesoreyeram-infinity-datasource` for your data source. You may click **Save and Test** if you wish.

![Screenshot of the default settings for the Infinity data source](../images/grafana_cloud_installed_infinity_datasource.png)

## Step 3: Import the Weather Dashboard 📝

Now that your Infinity data source is ready, it's time to import the weather dashboard.

1. Go to the **Dashboards** (four-square icon) on the left sidebar.

![Screenshot of the Grafana Cloud Dashboards link](../images/grafana_cloud_dashboards.png)

2. Click on **Import** at the top.

![Screenshot of the Grafana Cloud Import Dashboard button](../images/grafana_cloud_import_dashboard.png)

3. Upload the [weather-forecast.json](./weather-forecast.json) file that you can find in the 01-the-journey-begins folder of this repository. You may copy and paste the JSON or upload the entire file.

![Screenshot of the Grafana Cloud JSON for the weather dashboard](../images/grafana_cloud_copypasta_json.png)

4. During the import process, you will be prompted to select a data source. Choose the Infinity data source that you created in Step 2.

![Screenshot of the select data source pulldown](../images/grafana_cloud_select_datasource.png)

5. Click **Import** to load the dashboard.

6. Great work, now you have the default weather forecast dashboard for New York City.

![Screenshot of the default forecast panel for New York City](../images/grafana_cloud_nyc_weather_dashboard.png)

The URL at the top can be changed to show the weather forecast in any part of the United States. In the next step you'll find your local station URL and update the dashboard.

## Step 4: Get Your Weather API URL ⚙️

To make the weather dashboard work for your location, you need a special URL from the [National Weather Service](https://www.weather.gov/documentation/services-web-api). To find your URL you'll need to know your latitude and longitude.

1. Visit [maps.google.com](maps.google.com) and search for your location (or wherever you want your weather forecast). Right click on the location you want and you'll see a popup with the latitude and longitude. Click on the latitude and longitude to copy it to your clipboard.

![Screenshot of Area 51 on Google Maps](../images/google_maps_get_lat_long.png)

2. Open a new browser tab and type in this URL but don't hit enter yet!

```
https://api.weather.gov/points/
```

3. Right after the final slash, paste in the latitude and longitude you got from Google Maps.

> **⚠️ Important!**
> 
> There's a space after the comma that you must delete for the URL to work!

![Screenshot of the weather.gov API points URL](../images/weather_gov_points_url.png)

The final URL you end up at rounds the latitude and longitude to 4 digits. It will look like this:

```
https://api.weather.gov/points/42.5704,-73.6885
```

4. This JSON response contains data about your nearest detected NWS station. Scroll down until you see the "forecast" key under "properties":

![Screenshot of the api.weather.gov forecast URL](../images/weather_gov_forecast_url.png)

5. Copy the forecast URL for the next step.

## Step 5: Update the Dashboard with Your Weather URL 🗺️

Now that you have your gridpoint URL, let's update the dashboard to use it.

1. Open the weather dashboard you imported earlier.
2. At the top of the dashboard there's a text box with a URL in it. Replace it with your own forecast URL:

![Screenshot of the Grafana Cloud forecast URL variable text box](../images/grafana_cloud_paste_weather_url.png)

3. Notice how the weather forecast changes once you paste in the new URL.

## Step 6: Customize and Save Your Dashboard 💾

Next we'll rename the forecast panel on the dashboard.

1. Use the triple dot menu on the top right corner of the panel to select the **Edit** option.

![Screenshot of the Grafana Cloud edit panel menu](../images/grafana_cloud_edit_panel.png)

2. On the right side you'll see all your panel options. Update the panel's title to your own location.

![Screenshot of the Grafana Cloud panel being renamed](../images/grafana_cloud_rename_panel.png)

3. Save the dashboard with the button at the top of the page.

![Screenshot of the Grafana Cloud save dashboard button](../images/grafana_cloud_save_dashboard.png)

4. Add a note and make sure you select the checkbox to update your forecast default location.

![Screenshot of the Save Dashboard options, including a checkbox for default variable setting](../images/grafana_cloud_save_dashboard_2.png)

5. Use the "Back to Dashboard" button to return to the dashboard view.

![Screenshot of the Back to Dashboard link](../images/grafana_cloud_back_to_dashboard.png)

6. Congratulations, you completed the challenge!

![Screenshot of the renamed and updated dashboard](../images/grafana_cloud_area_51_weather.png)

## Step 7: Enjoy Your Custom Weather Forecast 🍾

You’ve completed your first challenge! Now, any time you want to check the weather, your magical forecast dashboard is just a click away.

> **🪄 Protip:**
> 
> Log onto your Grafana Cloud stack with your mobile device and add a bookmark to your home screen for quick access to your dashboard!

Congratulations, hero! You’ve learned how to:

- Sign up for Grafana Cloud.
- Enable a plugin and set up a data source.
- Import and customize a dashboard.
- Use the National Weather Service API to pull in live data.

Your journey is just beginning. Next up, you'll face your first true trial: **monitoring a Linux server**. 

Ready to take on the next challenge?

If you have an Ubuntu Linux VM, head over to [**02: The First Trial**](../02-the-first-trial/README.md) when you're ready!

If you don't have an Ubuntu VM or cloud instance, visit [**00: Prepare Your Equipment**](../00-prepare-your-equipment/README.md) to set up Virtualbox.
