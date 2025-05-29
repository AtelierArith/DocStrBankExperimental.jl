```
mutable struct TTN{T}
    sites::Vector{Index{T}}
    graph::Graph{Int2}
    tensors::Dict{Int2, ITensor}
    orthocenter::Int2
end
```

Tree Tensor Network (TTN) object.

Each tensor is indexed by the tuple of integers (`::Int2`), `(ll, nn)`, where (usually) `ll` denotes the layer index and `nn` denotes the tensor index at each layer.

  * `sites::Vector{Index}`: Physical site `Index`s.
  * `graph::Graph{Int2}`: Underlying structure of the network defined by `Graph{Int2}`.
  * `tensors::Dict{Int2, ITensor}`: Tensors in the TTN.
  * `orthocenter::Int2`: Orthogonality center of the TTN.
