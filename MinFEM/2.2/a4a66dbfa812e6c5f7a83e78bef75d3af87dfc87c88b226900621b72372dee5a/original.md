```
evaluate_function(
    f::Vector{Float64},
    node::Int64;
    qdim::Int64 = 1
) -> Vector{Float64}
```

Evaluates discrete function give as FEM coefficient vector at a given node. Resulting vector has the lenght of the number of components of f. 
