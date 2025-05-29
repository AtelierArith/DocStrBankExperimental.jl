```
(zone, isnorth) = utm_zone(lat, lon)
(zone, isnorth) = utm_zone(ll::LatLon)
(zone, isnorth) = utm_zone(lla::LLA)
(zone, isnorth) = utm_zone(ecef::ECEF, datum)
```

Find the UTM zone and hemisphere (`isnorth = true` or `false`) for the given latitude and longitude (or world point), including the special rules for Norway and Svalbard. Zone 0 corresponds to the poles, using the UPS regions.
