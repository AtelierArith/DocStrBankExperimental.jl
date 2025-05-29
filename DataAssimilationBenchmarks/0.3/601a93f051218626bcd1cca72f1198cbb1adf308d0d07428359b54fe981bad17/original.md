```
function ConM(type)
    Union{UniformScaling{T}, Symmetric{T}} where T <: type
end
```

Type union of conditioning matrix types, which are used for optimization routines in the transform method.
