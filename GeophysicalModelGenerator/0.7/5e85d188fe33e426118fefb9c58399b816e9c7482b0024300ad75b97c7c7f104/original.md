```
convert2UTMzone(d::GeoData, p::ProjectionPoint)
```

Converts a `GeoData` structure to fixed UTM zone, around a given `ProjectionPoint`     This useful to use real data as input for a cartesian geodynamic model setup (such as in LaMEM). In that case, we need to project map coordinates to cartesian coordinates.     One way to do this is by using UTM coordinates. Close to the `ProjectionPoint` the resulting coordinates will be rectilinear and distance in meters. The map distortion becomes larger the further you are away from the center.
