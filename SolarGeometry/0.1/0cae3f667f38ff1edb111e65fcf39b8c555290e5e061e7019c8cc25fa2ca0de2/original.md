```
function solar_azimuth_altitude(Δt, start_time::DateTime, lat, lon, alt)
```

Given a UTC time `start_time`, latitude `lat`, longitude `lon`, altitutde `alt` and offset `Δt`, return the solar azimuth and solar elevation angles (in degrees) relative to that location at `start_time + Δt`. This version of the function is to enable users to generate continuous output since DateTime does not allow for infinite precision seconds.
