```
naturalearth(name::String; version = v"5.1.2")
naturalearth(name::String, scale::Int; version = v"5.1.2")
```

Load a NaturalEarth dataset as a `GeoJSON.FeatureCollection` object.

The `name` should not include the `ne_` prefix, and if providing a `scale` should also not include a scale.  No suffix should be added.

For example, to get the `ne_110m_admin_0_countries` dataset, you could use:

```julia
naturalearth("admin_0_countries", 110)
naturalearth("110m_admin_0_countries")
```

We aim to support all datasets listed in https://github.com/nvkelso/natural-earth-vector/tree/master/geojson.

!!! warning
    This function downloads files from the Internet when not found locally.

