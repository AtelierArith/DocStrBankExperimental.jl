```
function TransM(type)
    Union{Tuple{Symmetric{T,Array{T,2}},Array{T,1},Array{T,2}},
          Tuple{Symmetric{T,Array{T,2}},Array{T,2},Array{T,2}}} where T <: type
end
```

Type union constructor for tuples representing the ensemble update step with a right ensemble anomaly transformation, mean update weights and mean-preserving orthogonal transformation.
