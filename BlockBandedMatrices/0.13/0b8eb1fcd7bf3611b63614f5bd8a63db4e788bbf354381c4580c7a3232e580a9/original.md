```
BlockBandedMatrix{T}(undef, rows::AbstractVector{Int}, cols::AbstractVector{Int},
                    (l,u)::NTuple{2,Int})
```

Return an unitialized `sum(rows) × sum(cols)` `BlockBandedMatrix` having `eltype` `T`, with `rows` by `cols` blocks and `(l,u)` as the block-bandwidth.
