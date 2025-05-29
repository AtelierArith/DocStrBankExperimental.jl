```
getraster(source::Type{EarthEnv{HabitatHeterogeneity}}, [layer]; res="25km")
```

Download [`EarthEnv`](@ref) habitat heterogeneity data.

# Arguments

  * `layer`: `Symbol` or `Tuple` of `Symbol` from `(:cv, :evenness, :range, :shannon, :simpson, :std, :Contrast, :Correlation, :Dissimilarity, :Entropy, :Homogeneity, :Maximum, :Uniformity, :Variance)`.   Without a `layer` argument, all layers will be downloaded, and a `NamedTuple` of paths returned.

# Keywords

  * `res`: `String` chosen from `("1km", "5km", "25km")`, defaulting to "25km".

Returns the filepath/s of the downloaded or pre-existing files.
