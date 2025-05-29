```julia
transform_solutions(
    res::HarmonicSteadyState.Result{D, S, ParType, F} where {ParType<:Number, F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}}},
    func;
    branches,
    realify
) -> Vector

```

Takes a `Result` object and a string `f` representing a Symbolics.jl expression. Returns an array with the values of `f` evaluated for the respective solutions. Additional substitution rules can be specified in `rules` in the format `("a" => val)` or `(a => val)`
