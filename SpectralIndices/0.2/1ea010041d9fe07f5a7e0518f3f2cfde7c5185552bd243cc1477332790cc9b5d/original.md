```
PlatformBand(platform_band::Dict{String, Any})
```

This struct provides information about a specific band for a specific sensor or platform.

# Arguments

  * `platform_band::Dict{String, Any}`: A dictionary with the following keys:

      * `"platform"`: Name of the platform or sensor.
      * `"band"`: Band number or name for the specific platform.
      * `"name"`: Description or name of the band for the specific platform.
      * `"wavelength"`: Center wavelength of the band (in nm) for the specific platform.
      * `"bandwidth"`: Bandwidth of the band (in nm) for the specific platform.

# Returns

A `PlatformBand` object containing the specified band information.

# Examples

```julia-repl
platform_band_dict = Dict(
    "platform" => "Sentinel-2A",
    "band" => "B2",
    "name" => "Blue",
    "wavelength" => 492.4,
    "bandwidth" => 66.0
)

platform_band = PlatformBand(platform_band_dict)
```

Or, accessing directly the provided Dict of platforms:

```julia-repl
julia> bands["B"].platforms["sentinel2a"]

```

```julia-repl
julia> bands["B"].platforms["sentinel2a"].wavelength

```
