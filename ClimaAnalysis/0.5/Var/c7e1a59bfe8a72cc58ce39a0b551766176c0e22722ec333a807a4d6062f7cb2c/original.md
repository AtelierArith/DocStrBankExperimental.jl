```
Var.convert_units(var, new_units; conversion_function = nothing)
```

Return a new `OutputVar` with converted physical units of `var` to `new_units`, if possible.

Automatic conversion happens when the units for `var` and `new_units` are both parseable. When `var` does not have units (see also [`Var.has_units`](@ref)) or has no parseable units, a conversion function `conversion_function` is required.

`conversion_function` has to be a function that takes one data point and returns the transformed value.

Being parseable means that `Unitful.uparse` can parse the expression. Please, refer to the documentation for [Unitful.jl](https://painterqubits.github.io/Unitful.jl/stable/) for more information.

# Examples

Let us set up a trivial 1D `OutputVar` with units of meters per second and automatically convert it to centimeters per second.

```jldoctest example1
julia> values = 0:100.0 |> collect;

julia> data = copy(values);

julia> attribs = Dict("long_name" => "speed", "units" => "m/s");

julia> dim_attribs = Dict{String, Dict}();

julia> var = ClimaAnalysis.OutputVar(attribs, Dict("distance" => values), dim_attribs, data);

julia> ClimaAnalysis.has_units(var)
true

julia> var_cms = ClimaAnalysis.convert_units(var, "cm/s");

julia> extrema(var_cms.data)
(0.0, 10000.0)
```

Not all the units can be properly parsed, for example, assuming `bob=5lol`

```jldoctest example1
julia> attribs = Dict("long_name" => "speed", "units" => "bob/s");

julia> var_bob = ClimaAnalysis.OutputVar(attribs, Dict("distance" => values), dim_attribs, data);

julia> var_lols = ClimaAnalysis.convert_units(var, "lol/s", conversion_function = (x) -> 5x);

julia> extrema(var_lols.data)
(0.0, 500.0)
```

Failure to specify the `conversion_function` will produce an error.
