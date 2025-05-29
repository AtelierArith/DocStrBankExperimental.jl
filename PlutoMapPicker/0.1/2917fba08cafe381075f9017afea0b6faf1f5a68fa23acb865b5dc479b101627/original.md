A tile layer that can be used in a Leaflet map.

The configuration includes:

  * `url`: a url template to request tiles
  * `options`: a `Dict` with extra configurations, such as a minimum and maximum zoom level of the tiles. This is interpolated to a Javascript object using HypertextLiteral.

The configuration is used to create a TileLayer in leaflet; see [leaflet's TileLayer documentation](https://leafletjs.com/reference.html#tilelayer) to read more about URL templates and the available options.
