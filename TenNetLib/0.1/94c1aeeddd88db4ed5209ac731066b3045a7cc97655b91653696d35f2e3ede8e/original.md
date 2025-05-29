```
mutable struct LinkProjTTN{T}
    tensors::Dict{LinkTypeTTN, ITensor}
    M::TTN{T}
end
```

Holds projectors at different links of the TTN. Required to calculate excited state or overlap with another state.

  * `tensors::Dict{LinkTypeTTN, ITensor}`: Tensors are each link.
  * `M::TTN`: The TTN to project.
