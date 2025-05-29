```
BandedBlockBandedMatrix{T}(undef, rows, cols, (l, u), (λ, μ))
```

初期化されていない `BandedBlockBandedMatrix` を返します。`eltype` は `T` で、ブロックバンド幅は `(l,u)` です。また、`A[Block(K,J)]` はサイズ `rows[K]×cols[J]` の `BandedMatrix{T}` で、バンド幅は `(λ,μ)` です。
