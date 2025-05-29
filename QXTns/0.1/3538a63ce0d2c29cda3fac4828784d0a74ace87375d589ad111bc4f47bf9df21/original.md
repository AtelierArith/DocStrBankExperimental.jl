```
QXTensor(data::AbstractArray{Elt, N},
         indices::Array{<:Index, 1};
         diagonal_check::Bool=true) where {Elt, N}
```

Constructor to create a QXTensor instance using the given data and indices. If diagonal*check is true, it will automaticallly check which indices are hyper indices and record in the hyper*indices field.
