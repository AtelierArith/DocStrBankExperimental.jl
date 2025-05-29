```
tocanonical(d, x)
```

点 `x` を `d` で `DomainSets.canonicaldomain(d)` の点にマップします。

# 例

```jldoctest
julia> tocanonical(0..0.5, 0)
-1.0

julia> tocanonical(0..0.5, 0.5)
1.0
```
