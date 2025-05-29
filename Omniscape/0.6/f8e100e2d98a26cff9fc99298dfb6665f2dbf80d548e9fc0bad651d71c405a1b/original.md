INI method:

```
run_omniscape(path::String)
```

In-memory method:

```
run_omniscape(
    cfg::Dict{String, String}
    resistance::MissingArray{Number, 2};
    reclass_table = MissingArray{Float64, 2}(undef, 1, 2),
    source_strength = source_from_resistance(resistance, cfg, reclass_table),
    condition1 = MissingArray{Float64, 2}(undef, 1, 1),
    condition2 = MissingArray{Float64, 2}(undef, 1, 1),
    condition1_future = MissingArray{Float64, 2}(undef, 1, 1),
    condition2_future = MissingArray{Float64, 2}(undef, 1, 1),
    wkt = "",
    geotransform = [0.0, 1.0, 0.0, 0.0, 0.0, -1.0],
    write_outputs = false
)
```

Compute omnidirectional current flow. All array inputs for the in-memory method should be of type `MissingArray{T, 2}`, which is just an alias for `Array{Union{Missing, T}, 2}`. `missing` entries correspond to NoData pixels. If you are starting with an array with a numeric NoData value, use  [`missingarray`](@ref) to convert it to a `MissingArray`. 

# Parameters

**`path`**: The path to an INI file containing run parameters. See the [Settings and Options](@ref) section of the User Guide for descriptions of the run parameters.

**`cfg`**: A dictionary of Omniscape run parameters. See the [Settings and Options](@ref) section of the User Guide for descriptions of the run parameters and their default values. The in-memory method of `run_omniscape` ignores the following keys: `resistance_file`, `source_file`, `reclass_table`, `condition1_file`, `condition2_file`, `condition1_future_file`, and `condition2_future_file`. These all specify file paths, so they do not apply to the in-memory method of `run_omniscape`.

**`resistance`**: A 2D, north-oriented array of resistance values. Use `missing` for NoData (infinite resistance). `resistance` cannot contain zeros or negative values.

# Keyword Arguments

**`reclass_table`**:  A two column array. The first column contains the original resistance values in the resistance surface, and the second column specifies what those values should be changed to. You can reclassify values to `missing` to replace them with infinite resistance (NoData).

**`source_strength`**: A 2D, north-oriented array (with size equal to `size(resistance)`) of source strength values. `source_strength` is only required if `source_from_resistance` in `cfg` is set to "false" (the default value).

**`condition1`**: Optional. Required if `conditional` in`cfg` is set to "true". A 2D, north-oriented array (with size equal to `size(resistance)`). See [Climate Connectivity](@ref) and [Conditional Connectivity Options](@ref) for more information.

**`condition2`**: Optional. Required if `conditional` in`cfg` is set to "true" and `n_conditions` in `cfg` is set to "2". A 2D, north-oriented array (with size equal to `size(resistance)`). See [Climate Connectivity](@ref) and [Conditional Connectivity Options](@ref) for more information.

**`condition1_future`**: Optional. Required if `conditional` in `cfg` is set to "true" and `compare_to_future` in `cfg` is set to "1" or "both". A 2D, north-oriented array (with size equal to `size(resistance)`). See [Climate Connectivity](@ref) and [Conditional Connectivity Options](@ref) for more information.

**`condition2_future`**: Optional. A 2D, north-oriented array (with size equal to `size(resistance)`). See [Climate Connectivity](@ref) and [Conditional Connectivity Options](@ref) for more information. Required if `conditional` in`cfg` is set to "true", `n_conditions` in `cfg` is set to "2", and `compare_to_future` in `cfg` is set to "2" or "both".

**`wkt`**: Optionally specify a Well Known Text representation of the projection used for your spatial data inputs. Only used if Omniscape writes raster outputs to disk.

**`geotransform`**: In addition to `wkt`, optionally specify a geotransform. The geotransform is a 6-element vector with elements as follows for a north up oriented image: `[<x coord of upper left orner>, <pixel width>, <row rotation (typically 0)>, <y coord of upper left corner>, <column rotation (typically 0)>, <pixel height (negative number)>]`. Only used when writing raster outputs to disk.

**`write_outputs`**: Boolean specifying if outputs should be written to disk. Defaults to `false`. If `true`, `cfg` must contain a value for the `project_name` key.
