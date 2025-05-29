```
BandedBlockBandedMatrix{T}(undef, rows, cols, (l, u), (λ, μ))
```

Return an unitialized `BandedBlockBandedMatrix` having `eltype` `T`, with block-bandwidths `(l,u)` and where `A[Block(K,J)]` is a `BandedMatrix{T}` of size `rows[K]×cols[J]` with bandwidths `(λ,μ)`.
