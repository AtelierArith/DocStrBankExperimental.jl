```
applymap!(result::Matrix, K::Vector{<:AbstractMatrix}, M::AbstractMatrix, temp::Matrix)
```

Applies the CP map given by the Kraus operators `K` to the matrix `M` without allocating or wrapping. `result` and `temp` must be matrices of size `dout × dout` and `dout × din`, where `dout, din == size(K[1])`.
