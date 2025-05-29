```
prefixsum(ft::FenwickTree{T}, ind::Integer)
```

インデックス1から`ind`までの累積和を[`FenwickTree`](@ref)から返します。

# 例

```
julia> f = FenwickTree{Int}(6)
julia> inc!(f, 2, 5)
julia> prefixsum(f, 1)
 0
julia> prefixsum(f, 3)
 5
```
