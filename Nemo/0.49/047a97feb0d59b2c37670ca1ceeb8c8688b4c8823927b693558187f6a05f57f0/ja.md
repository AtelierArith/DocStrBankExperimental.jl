```
(ZZ::ZZRing)(x)
```

`x`を$\mathbb Z$の要素に強制変換します。`ZZ(x)`は[`ZZRingElem(x)`](@ref)と同等です。

# 例

```jldoctest
julia> ZZ(2)
2

julia> ZZ(2)^100
1267650600228229401496703205376
```
