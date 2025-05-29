```
stability_region(z, alg::AbstractODEAlgorithm)
```

Calculates the stability function from the algorithm `alg` at `z`. The stability region of a possible embedded method cannot be calculated using this method.

If you use an implicit method, you may run into convergence issues when the value of `z` is outside of the stability region, e.g.,

```julia-repl
julia> typemin(Float64)
-Inf

julia> stability_region(typemin(Float64), ImplicitEuler())
┌ Warning: Newton steps could not converge and algorithm is not adaptive. Use a lower dt.

julia> nextfloat(typemin(Float64))
-1.7976931348623157e308

julia> stability_region(nextfloat(typemin(Float64)), ImplicitEuler())
0.0
```
