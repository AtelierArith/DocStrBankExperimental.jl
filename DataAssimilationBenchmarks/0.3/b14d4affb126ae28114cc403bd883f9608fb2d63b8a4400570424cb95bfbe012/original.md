```
function CovM(type)
    Union{UniformScaling{T}, Diagonal{T, Vector{T}},
          Symmetric{T, Matrix{T}}} where T <: type
end
```

Type constructor for union of covariance matrix types, for multiple dispatch based on their special characteristics as symmetric, positive definite operators.
