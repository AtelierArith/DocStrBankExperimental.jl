```
PlotLayoutGeo()
```

---

# Examples

---

```
julia>
```

---

# Properties

---

  * `bgcolor::String` - Set the background color of the map.  Type: `color` | Default: `"#fff"`
  * `center::Mcenter` - Check Mcenter documentation for details.
  * `coastlinecolor::String` - Set the coastline color.  Type: `color` | Default: `"#444"`
  * `coastlinewidth::Int` - Set the coastline width.  Type: `number` | Default: `1`
  * `countrywidth::Int` - Sets line color of the country boundaries. Type: number greater than or equal to `0` | Default: `1`
  * `fitbounds::Bool` - Determines if this subplot's view settings are auto-computed to fit trace data. On scoped maps, setting `fitbounds` leads to `center.lon` and `center.lat` getting auto-filled. On maps with a non-clipped projection, setting `fitbounds` leads to `center.lon`, `center.lat`, and `projection.rotation.lon` getting auto-filled. On maps with a clipped projection, setting `fitbounds` leads to `center.lon`, `center.lat`, `projection.rotation.lon`, `projection.rotation.lat`, `lonaxis.range` and `lonaxis.range` getting auto-filled. If "locations", only the trace's visible locations are considered in the `fitbounds` computations. If "geojson", the entire trace input `geojson` (if provided) is considered in the `fitbounds` computations, Defaults to "false". Type: enumerated , one of ( false | "locations" | "geojson" )
  * `framecolor::String` - Set the frame color.  Type: `color` | Default: `"#444"`
  * `framewidth::Int` - Sets the stroke width (in px) of the frame. Type: number greater than or equal to `0` | Default: `1`
  * `lakecolor::String` - Set the color of the lakes.  Type: `color` | Default: `"#3399FF"`
  * `landcolor::String` - Sets the land mass color. Type: `color` | Default: `"#F0DC82"`
  * `lataxis::PlotLayoutAxis` - Check PlotLayoutAxis documentation for details.
  * `lonaxis::PlotLayoutAxis` - Check PlotLayoutAxis documentation for details.
  * `oceancolor::String` - Sets the ocean color. Type: `color` | Default: `"#3399FF"`
  * `geoprojection::GeoProjection` - Check GeoProjection documentation for details.
  * `resolution::String` - Sets the resolution of the base layers. The values have units of km/mm e.g. 110 corresponds to a scale ratio of `1:110,000,000`. Type: enumerated , one of ( `"110"` | `"50"` ) | Default: `"110"`
  * `rivercolor::String` - Sets color of the rivers. Type: `color` | Default: `"#3399FF"`
  * `riverwidth::Int` - Sets the stroke width (in px) of the rivers. Type: number greater than or equal to `0` | Default: `1`
  * `scope::String` - Sets the scope of the map. Type: enumerated , one of ( `"world"` | `"usa"` | `"europe"` | `"asia"` | `"africa"` | `"north america"` | `"south america"` ) | Default: `"world"`
  * `showcoastlines::Bool` - Sets whether or not the coastlines are drawn.
  * `showcountries::Bool` - Sets whether or not country boundaries are drawn.
  * `showframe::Bool` - Sets whether or not a frame is drawn around the map.
  * `showlakes::Bool` - Sets whether or not lakes are drawn.
  * `showland::Bool` - Sets whether or not land masses are filled in color.
  * `showocean::Bool` - Sets whether or not oceans are filled in color.
  * `showrivers::Bool` - Sets whether or not rivers are drawn.
  * `showsubunits::Bool` - Sets whether or not boundaries of subunits within countries (e.g. states, provinces) are drawn.
  * `subunitcolor::String` - Sets the color of the subunits boundaries. Type: `color` | Default: `"#444"`
  * `subunitwidth::Int` - Sets the stroke width (in px) of the subunits boundaries. Type: number greater than or equal to `0` | Default: `1`
  * `uirevision::Union{String,Int}` - Controls persistence of user-driven changes in the view (projection and center). Defaults to `layout.uirevision`.  Type: number or categorical coordinate string
  * `visible::Bool` - Sets the default visibility of the base layers. Default: `true`
