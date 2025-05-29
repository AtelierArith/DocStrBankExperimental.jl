```
Provider

Provider(url; name=nothing, max_zoom=18, attribution="")
```

Defines the parameters of a base layer tile provider, such as `OSM`, `Esri` etc.

`Provider` can also be defined manually for custom tile providers.

# Arguments

  * `url`: URL tile path, e.g. "http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"

# Keywords

  * `name`: A `Symbol` name for the provider, or `nothing`

# Example

Manually define an OpenStreetMap provider.

```julia
using Blink, Leaflet

```

julia url = "http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png" provider = Leaflet.Provider(url)

w = Blink.Window() body!(w, Leaflet.Map(; provider, zoom=3, height=1000))
