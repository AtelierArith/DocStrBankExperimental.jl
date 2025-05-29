```
DiagOfProd(P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
```

**エイリアス**: `dop`

2つの `Hermitian` 行列 `P` と `Q` の積 $PQ$ の対角成分を保持する `Diagonal` 行列を返します。積の対角部分のみが計算されます。

**関連項目**: [`tr`](@ref), [`fDiag`](@ref).

**例**

```julia
using PosDefManifold, LinearAlgebra
P, Q=randP(5), randP(5)
DiagOfProd(P, Q)≈Diagonal(P*Q) ? println("⭐ ") : println("⛔ ")
```
