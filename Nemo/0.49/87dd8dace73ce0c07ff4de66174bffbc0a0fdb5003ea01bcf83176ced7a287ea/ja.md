```
lift(::ZZRing, x::FqFieldElem) -> ZZRingElem
```

素数体 $\mathbf{F}_p$ の要素 $x$ が与えられたとき、標準的な写像 $\mathbf{Z} \to \mathbf{F}_p$ の下での前像を返します。

# 例

```jldoctest
julia> K = GF(19);

julia> lift(ZZ, K(3))
3
```
