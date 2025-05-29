```
FiniteMPO(Os::Vector{O}) -> FiniteMPO{O}
FiniteMPO(O::AbstractTensorMap{S,N,N}) where {S,N} -> FiniteMPO{O<:MPOTensor}
```

有限テンソル積空間に線形順序で作用する行列積演算子 (MPO)。
