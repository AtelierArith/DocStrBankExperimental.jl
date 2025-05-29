```
(x,z)=get_degopt_crefs(k)
(x,z)=get_degopt_crefs(graph)
```

Returns linear combination references (crefs) related to [`graph_degopt`](@ref). Specifically `x` is a `Vector{Tuple{Vector{Tuple{Symbol,Int}},Vector{Tuple{Symbol,Int}}}}` such that `x[2][1]` corresponds to the coefficients of the left hand side of the multiplication

```
B2=(α_2_1 *I + α_2_2 *A)(β_2_1 *I + β_2_2 *A)
```

i.e., the crefs corresponding to `[α_2_1, α_2_2]`. See [`graph_degopt`](@ref). Hence, `get_coeffs(graph,x[2][1])` returns the corresponding numerical values of the coefficients.
