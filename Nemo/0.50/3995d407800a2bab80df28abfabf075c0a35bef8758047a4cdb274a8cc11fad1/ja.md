```
ZZRing <: Ring
ZZRingElem <: RingElem
```

整数の環 $\mathbb Z$ とその要素。便利のために、グローバル変数 `const ZZ = ZZRing()` を事前に定義しておきます。これにより、[`ZZ(x)`](@ref `(::Ring)(x)`) を介して要素を作成できます。

# 例

```jldoctest
julia> ZZ(2)
2

julia> ZZ(2)^100
1267650600228229401496703205376
```
