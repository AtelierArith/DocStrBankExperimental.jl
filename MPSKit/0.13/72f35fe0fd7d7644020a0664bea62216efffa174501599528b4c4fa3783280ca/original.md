```
FiniteMPO(Os::Vector{O}) -> FiniteMPO{O}
FiniteMPO(O::AbstractTensorMap{S,N,N}) where {S,N} -> FiniteMPO{O<:MPOTensor}
```

Matrix Product Operator (MPO) acting on a finite tensor product space with a linear order.
