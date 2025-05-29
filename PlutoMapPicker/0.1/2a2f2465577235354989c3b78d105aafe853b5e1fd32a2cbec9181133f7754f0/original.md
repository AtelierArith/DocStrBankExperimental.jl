Create an interactive map to pick multiple locations

Basic usage in a Pluto notebook:

```julia
@bind places MapPickerMultiple(0.0, 0.0, 1)
```

Uses [Leaflet](https://leafletjs.com/) to render a map. By default, the map uses tiles from OpenStreetMap. Please read OSM's [usage policy](https://operations.osmfoundation.org/policies/tiles/).

Users can place and remove markers on the map to select locations. If you use `@bind` in Pluto, your bound variable will receive an array with the coordinates for each selected point. Each point is provided as a `Dict` with keys `"lat"` and `"lng"`.

Input:

You have to supply the latitude and longitude that the map should initially centre on, as well as the initial zoom level.

Additional parameters:

  * `tile_layer`: a `TileLayer` configuration.
  * `height`: height of the map in pixels.
