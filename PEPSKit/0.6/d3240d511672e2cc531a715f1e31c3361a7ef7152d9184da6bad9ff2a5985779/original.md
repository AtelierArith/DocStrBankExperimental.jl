```
InfiniteWeightPEPS(vertices::Matrix{T}, weight_mats::Matrix{E}...) where {T<:PEPSTensor,E<:PEPSWeight}
```

Create an InfiniteWeightPEPS from matrices of vertex tensors, and separate matrices of weights on each type of bond at all locations in the unit cell.
