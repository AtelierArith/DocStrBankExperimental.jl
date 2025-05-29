Create an interactive map to pick a location.

Basic usage in a Pluto notebook:

```julia
@bind place MapPicker(0.0, 0.0, 1)
```

Uses [Leaflet](https://leafletjs.com/) to render a map. By default, the map uses tiles from OpenStreetMap. Please read OSM's [usage policy](https://operations.osmfoundation.org/policies/tiles/).

Users can place a marker on the map to select a location. If you use `@bind` in Pluto, your bound variable will receive the coordinates in a `Dict` with keys `"lat"` and `"lng"`, or `nothing` if no marker has been placed.

Input:

You have to supply the latitude and longitude that the map should initially centre on, as well as the initial zoom level.

Additional parameters:

  * `tile_layer`: a `TileLayer` configuration.
  * `height`: height of the map in pixels.
