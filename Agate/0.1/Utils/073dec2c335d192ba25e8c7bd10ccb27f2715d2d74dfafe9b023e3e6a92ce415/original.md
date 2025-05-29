```
define_tracer_functions(
    parameters,
    tracers;
    auxiliary_fields=[:PAR],
    helper_functions=nothing,
    sinking_tracers=nothing,
    grid=nothing,
    open_bottom=false,
) -> DataType
```

Create an Oceananigans.Biogeochemistry model type.

# Arguments

  * `parameters`: named sequence of values of the form ((<field name> = <default value>, ...)
  * `tracers`: dictionary of the form (<name> => <expression>, ...)

# Keywords

  * `auxiliary_fields`: an iterable of auxiliary field variables, defaults to `[:PAR,]`
  * `helper_functions`: optional path to a file of helper functions used in tracer expressions
  * `sinking_tracers`: optional NamedTuple of sinking speeds (passed as positive values) of  the form (<tracer name> = <speed>, ...)
  * `grid`: optional Oceananigans grid object defining the geometry to build the model on, must  be passed if `sinking_tracers` is defined
  * `open_bottom`: indicates whether the sinking velocity should be smoothly brought to zero  at the bottom to prevent the tracers leaving the domain, defaults to `true`, which means  the bottom is open and the tracers leave (i.e., no slowing of velocity to 0 is applied)

Note that the field names defined in `parameters` can't be any of [:x, :y, :z, :t], as these are reserved for coordinates, and they must include all parameters used in the `tracers` expressions. The expressions must use methods that are either defined within this module or passed in the `helper_functions` file.

# Example

```julia
using Agate

parameters = (α=2 / 3, β=4 / 3, δ=1, γ=1)
tracers = Dict("R" => :(α * R - β * R * F), "F" => :(-γ * F + δ * R * F))
LV = define_tracer_functions(parameters, tracers)
```
