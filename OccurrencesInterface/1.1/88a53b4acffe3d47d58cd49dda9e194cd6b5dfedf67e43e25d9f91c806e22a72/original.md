```
place(o::Occurrence)
```

Returns the place of the occurrence event, either as a tuple of float in the longitude, latitude format, or as `missing`. The CRS is assumed to be WGS84 with no option to change it. This follows the GeoJSON specification.
