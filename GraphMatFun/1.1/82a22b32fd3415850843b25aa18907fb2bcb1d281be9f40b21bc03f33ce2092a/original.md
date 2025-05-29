```
 (graph,crefs)=graph_exp_native_jl_degopt(A; input=:A)
```

Same as [`graph_exp_native_jl`](@ref) but with calls to [`graph_degopt`](@ref) for contruction of numerator and denominator polynomials.
