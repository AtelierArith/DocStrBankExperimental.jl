```
evaluate_quadrature_function(
    mesh::Mesh,
    f::Function,
    region::Set{Domain};
    order::Int64 = 1, 
    qdim::Int64 = 1
) -> Vector{Float64}
```

Same as previous evaluate*quadrature*function(...) but takes `Set{Domain}` as mandatory argument for the relevant region, which replaces the keyword argument using `Set{Int64}`. Extracts nodes from the domain and then passes them to the base function. 
