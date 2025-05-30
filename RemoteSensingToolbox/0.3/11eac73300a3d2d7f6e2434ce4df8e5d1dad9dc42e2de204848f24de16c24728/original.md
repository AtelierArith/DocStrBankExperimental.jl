```
plot_signatures!(ax, bandset::Type{<:AbstractSatellite}, sigs; kwargs...)
plot_signatures!(ax, bandset::Vector{<:Pair}, sigs; colors=Makie.wong_colors(), label=:label)
```

Plot the spectral signatures for one or more land cover types onto an existing `Makie.Axis`.

# Parameters

  * `ax`: The `Makie.Axis` onto which to plot the signatures.
  * `bandset`: An `AbstractSatellite` or a vector of sorted `band => wavelength` pairs.
  * `sigs`: A table whose rows consist of spectral signatures and their associated labels.

# Keywords

  * `label`: The column in `sigs` containing the signature labels (default = `:label`).
  * `colors`: The color scheme used by the plot (default = `Makie.wong_colors()`).

# Example

```julia
using RemoteSensingToolbox, Rasters, GeoDataFrames, Statistics, CairoMakie

# Read Images And Convert DNs To Reflectance
landsat = Landsat8("data/LC08_L2SP_043024_20200802_20200914_02_T1/")
sentinel = Sentinel2{20}("data/T11UPT_20200804T183919/")
landsat_reflectance = decode(Landsat8, RasterStack(landsat))
sentinel_reflectance = decode(Sentinel2, RasterStack(sentinel))

# Read Landcover Labels From Shapefile
shp = GeoDataFrames.read("data/landcover/landcover.shp")

# Extract Average Spectral Signature For Each Landcover Type
landsat_sigs = extract_signatures(mean, landsat_reflectance, shp, :MC_name)
sentinel_sigs = extract_signatures(mean, sentinel_reflectance, shp, :MC_name)

# Create Figure and Axis
fig = Figure(resolution=(800,550));
ax1 = Axis(fig[1,1], ylabel="Reflectance", title="Landsat Signatures")
ax2 = Axis(fig[2,1], xlabel="Wavelength (nm)", ylabel="Reflectance", title="Sentinel Signatures")

# Plot Signatures
plot_signatures!(ax1, Landsat8, landsat_sigs, colors=[:brown, :orange, :blue, :green])
plot_signatures!(ax2, Sentinel2{20}, sentinel_sigs, colors=[:brown, :orange, :blue, :green])

# Add Legend
Legend(fig[:,2], ax1)
```
