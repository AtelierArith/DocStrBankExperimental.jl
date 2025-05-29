```julia
classify_solutions!(
    res::HarmonicSteadyState.Result,
    func::Union{Function, String},
    name::String;
    physical
) -> Any

```

Creates a solution class in `res` using the function `func` (parsed into Symbolics.jl input). The new class is labeled with `name` and stored under `res.classes[name]`. By default, only physical (real) solutions are classified, and `false` is returned for the rest. To also classify complex solutions, set `physical=false`.

# Example

```julia
# solve a previously-defined problem
res = get_steady_states(problem, swept_parameters, fixed_parameters)

# classify, store in result.classes["large_amplitude"]
classify_solutions!(res, "sqrt(u1^2 + v1^2) > 1.0" , "large_amplitude")
```
