```
findfirst(pattern::AbstractVector{<:Union{Int8,UInt8}},
          A::AbstractVector{<:Union{Int8,UInt8}})
```

ベクトル `A` の中でシーケンス `pattern` の最初の出現を見つけます。

!!! compat "Julia 1.6"
    このメソッドは少なくとも Julia 1.6 が必要です。


# 例

```jldoctest
julia> findfirst([0x52, 0x62], [0x40, 0x52, 0x62, 0x63])
2:3
```
