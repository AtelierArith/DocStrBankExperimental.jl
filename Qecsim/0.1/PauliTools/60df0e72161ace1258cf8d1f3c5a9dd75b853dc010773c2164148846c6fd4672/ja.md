```
weight(pauli::Union{AbstractString,AbstractVector{<:AbstractString}}) -> Int
```

パウリ文字列演算子の重みを返します。

# 例

```jldoctest
julia> weight("XIZIY")
3
```

```jldoctest
julia> weight(["XIZIY", "XXXXX"])
8
```
