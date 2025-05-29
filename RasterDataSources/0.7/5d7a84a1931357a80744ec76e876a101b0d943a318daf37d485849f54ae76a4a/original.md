```
getraster(T::Type{EarthEnv{LandCover}}, [layer]; discover=false) => Union{Tuple,String}
```

Download [`EarthEnv`](@ref) landcover data.

# Arguments

  * `layer`: `Integer` or tuple/range of `Integer` from `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12)`,   or `Symbol`s from `(:needleleaf_trees, :evergreen_broadleaf_trees, :deciduous_broadleaf_trees, :other_trees, :shrubs, :herbaceous, :cultivated_and_managed, :regularly_flooded, :urban_builtup, :snow_ice, :barren, :open_water)`. Without a `layer` argument,   all layers will be downloaded, and a `NamedTuple` of paths returned.

# Keywords

  * `discover::Bool`: whether to download the dataset that integrates the DISCover model.

Returns the filepath/s of the downloaded or pre-existing files.
