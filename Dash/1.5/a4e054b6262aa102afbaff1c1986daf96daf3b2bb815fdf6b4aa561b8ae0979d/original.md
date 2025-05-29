```
dcc_geolocation(;kwargs...)
```

A Geolocation component The CurrentLocation component gets geolocation of the device from the web browser.  See more info here: https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API

  * `id` (String; optional): The ID used to identify this component in Dash callbacks.
  * `high_accuracy` (Bool; optional): If true and if the device is able to provide a more accurate position,

it will do so. Note that this can result in slower response times or increased power consumption (with a GPS  chip on a mobile device for example). If false (the default value), the device can save resources by  responding more quickly and/or using less power.

  * `local_date` (String; optional): The local date and time when the device position was updated.

Format:  MM/DD/YYYY, hh:mm:ss p   where p is AM or PM

  * `maximum_age` (optional): The maximum age in milliseconds of a possible cached position that is acceptable to return. If set to 0,

it means that the device cannot use a cached position and must attempt to retrieve the real current position. If set to Infinity the device must return a cached position regardless of its age. Default: 0.

  * `position` (lists containing elements lat, lon, accuracy, alt, alt*accuracy, heading, speed   - `lat` (optional)   - `lon` (optional)   - `accuracy` (optional)   - `alt` (optional)   - `alt*accuracy`(optional)   -`heading`(optional)   -`speed`(optional); optional): The position of the device.`lat`,`lon`, and`accuracy` will always be returned.  The other data will be included

when available, otherwise it will be NaN.

```
  `lat` is latitude in degrees.
  `lon` is longitude in degrees.
  `accuracy` is the accuracy of the lat/lon in meters.    *

  `alt` is altitude above mean sea level in meters.
  `alt_accuracy` is the accuracy of the altitude  in meters.
  `heading` is the compass heading in degrees.
  `speed` is the  speed in meters per second.
```

  * `position_error` (lists containing elements code, message   - `code` (optional)   - `message` (String; optional); optional): Position error
  * `show_alert` (Bool; optional): If true, error messages will be displayed as an alert
  * `timeout` (optional): The maximum length of time (in milliseconds) the device is allowed to take in order to return a position.

The default value is Infinity, meaning that data will not be return until the position is available.

  * `timestamp` (optional): The Unix timestamp from when the position was updated
  * `update_now` (Bool; optional): Forces a one-time update of the position data.   If set to True in a callback, the browser will update the position data and reset update_now back to False.  This can, for example, be used to update the

position with a button or an interval timer.
