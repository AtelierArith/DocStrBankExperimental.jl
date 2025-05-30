```
plot_signatures(bandset::Type{<:AbstractSatellite}, sigs; kwargs...)
plot_signatures(bandset::Vector{<:Pair}, sigs; colors=Makie.wong_colors(), label=:label)
```

Plot the spectral signatures for one or more land cover types.

# Parameters

  * `bandset`: An `AbstractSatellite` or a vector of sorted `band => wavelength` pairs.
  * `sigs`: A table whose rows consist of spectral signatures and their associated labels.

# Keywords

  * `label`: The column in `sigs` containing the signature labels (default = `:label`).
  * `colors`: The color scheme used by the plot (default = `Makie.wong_colors()`).

# Example

```julia
julia> src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1");

julia> surface_reflectance = decode(Landsat8, RasterStack(src));

julia> shp = GeoDataFrames.read("data/landcover/landcover.shp");

julia> sigs = extract_signatures(mean, surface_reflectance, shp, :MC_name);

julia> plot_signatures(Landsat8, sigs, colors=[:brown, :orange, :blue, :green])
```
