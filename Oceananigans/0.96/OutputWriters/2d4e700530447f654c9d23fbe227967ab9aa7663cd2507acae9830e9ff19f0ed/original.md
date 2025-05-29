```
JLD2Writer(model, outputs; filename, schedule,
           dir = ".",
           indices = (:, :, :),
           with_halos = true,
           array_type = Array{Float32},
           file_splitting = NoFileSplitting(),
           overwrite_existing = false,
           init = noinit,
           including = [:grid, :coriolis, :buoyancy, :closure],
           verbose = false,
           part = 1,
           jld2_kw = Dict{Symbol, Any}())
```

Construct a `JLD2Writer` for an Oceananigans `model` that writes `label, output` pairs in `outputs` to a JLD2 file.

The argument `outputs` may be a `Dict` or `NamedTuple`. The keys of `outputs` are symbols or strings that "name" output data. The values of `outputs` are either `AbstractField`s, objects that are called with the signature `output(model)`, or `WindowedTimeAverage`s of `AbstractFields`s, functions, or callable objects.

# Keyword arguments

## Filenaming

  * `filename` (required): Descriptive filename. `".jld2"` is appended to `filename` in the file path                        if `filename` does not end in `".jld2"`.
  * `dir`: Directory to save output to. Default: `"."` (current working directory).

## Output frequency and time-averaging

  * `schedule` (required): `AbstractSchedule` that determines when output is saved.

## Slicing and type conversion prior to output

  * `indices`: Specifies the indices to write to disk with a `Tuple` of `Colon`, `UnitRange`,            or `Int` elements. Indices must be `Colon`, `Int`, or contiguous `UnitRange`.            Defaults to `(:, :, :)` or "all indices". If `!with_halos`,            halo regions are removed from `indices`. For example, `indices = (:, :, 1)`            will save xy-slices of the bottom-most index.
  * `with_halos` (Bool): Whether or not to slice off or keep halo regions from fields before writing output.                      Preserving halo region data can be useful for postprocessing. Default: true.
  * `array_type`: The array type to which output arrays are converted to prior to saving.               Default: `Array{Float32}`.

## File management

  * `file_splitting`: Schedule for splitting the output file. The new files will be suffixed with                   `_part1`, `_part2`, etc. For example `file_splitting = FileSizeLimit(sz)` will                   split the output file when its size exceeds `sz`. Another example is                   `file_splitting = TimeInterval(30days)`, which will split files every 30 days of                   simulation time. The default incurs no splitting (`NoFileSplitting()`).
  * `overwrite_existing`: Remove existing files if their filenames conflict.                       Default: `false`.

## Output file metadata management

  * `init`: A function of the form `init(file, model)` that runs when a JLD2 output file is initialized.         Default: `noinit(args...) = nothing`.
  * `including`: List of model properties to save with every file.              Default: `[:grid, :coriolis, :buoyancy, :closure]`

## Miscellaneous keywords

  * `verbose`: Log what the output writer is doing with statistics on compute/write times and file sizes.            Default: `false`.
  * `part`: The starting part number used when file splitting.         Default: 1.
  * `jld2_kw`: Dict of kwargs to be passed to `jldopen` when data is written.

# Example

Write out 3D fields for $u$, $v$, $w$, and a tracer $c$, along with a horizontal average:

```@example
using Oceananigans
using Oceananigans.Utils: hour, minute

model = NonhydrostaticModel(grid=RectilinearGrid(size=(1, 1, 1), extent=(1, 1, 1)), tracers=:c)
simulation = Simulation(model, Δt=12, stop_time=1hour)

function init_save_some_metadata!(file, model)
    file["author"] = "Chim Riggles"
    file["parameters/coriolis_parameter"] = 1e-4
    file["parameters/density"] = 1027
    return nothing
end

c_avg =  Field(Average(model.tracers.c, dims=(1, 2)))

# Note that model.velocities is NamedTuple
simulation.output_writers[:velocities] = JLD2Writer(model, model.velocities,
                                                    filename = "some_data.jld2",
                                                    schedule = TimeInterval(20minute),
                                                    init = init_save_some_metadata!)
```

and a time- and horizontal-average of tracer $c$ every 20 minutes of simulation time to a file called `some_averaged_data.jld2`

```@example
simulation.output_writers[:avg_c] = JLD2Writer(model, (; c=c_avg),
                                               filename = "some_averaged_data.jld2",
                                               schedule = AveragedTimeInterval(20minute, window=5minute))
```
