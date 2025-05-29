```
const ElementInfo{T}=Union{Vector{T},VectorOfConstants{T}}
```

Union type for element information arrays. If all elements have the same information, it can be stored in an economical form as a [`VectorOfConstants`](@ref).
