```
QXTensor(indices::Array{<:Index, 1},
         hyper_indices::Array{<:Array{Int64, 1}, 1},
         storage::Union{Nothing, <: NDTensors.TensorStorage}=nothing)
```

QXTensor constructor which creates a new instance of QXTensor with the given indices and hyper indices. If no storage data structure is given then MockTensor of that shape is added as the storage.
