```
BlockBandedMatrix{T}(undef, rows::AbstractVector{Int}, cols::AbstractVector{Int},
                    (l,u)::NTuple{2,Int})
```

`eltype` `T` を持ち、`rows` と `cols` のブロックを持ち、ブロックバンド幅が `(l,u)` の `sum(rows) × sum(cols)` の初期化されていない `BlockBandedMatrix` を返します。
