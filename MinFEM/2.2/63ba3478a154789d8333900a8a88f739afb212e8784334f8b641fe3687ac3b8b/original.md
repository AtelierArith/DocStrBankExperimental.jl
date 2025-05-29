```
evaluate_function(
    f::Vector{Float64},
    region::Set{Int64};
    qdim::Int64 = 1
) -> Vector{Float64}
```

Evaluates discrete function give as FEM coefficient vector at all nodes in a given region. Resulting vector has the lenght of the full coefficient vector with the entries corresponding to non-evaluated nodes being zero. 
