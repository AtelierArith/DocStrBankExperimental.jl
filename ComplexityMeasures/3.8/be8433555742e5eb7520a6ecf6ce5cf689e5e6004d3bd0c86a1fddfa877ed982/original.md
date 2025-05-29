```
transfermatrix(iv::InvariantMeasure) → (M::AbstractArray{<:Real, 2}, bins::Vector{<:SVector})
```

Return the transfer matrix/operator and corresponding bins. Here, `bins[i]` corresponds to the i-th row/column of the transfer matrix. Thus, the entry `M[i, j]` is the probability of jumping from the state defined by `bins[i]` to the state defined by `bins[j]`.

See also: [`TransferOperator`](@ref).
