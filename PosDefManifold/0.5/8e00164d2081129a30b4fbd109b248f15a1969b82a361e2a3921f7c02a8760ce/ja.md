```
(1) invsqrt(P{T}::ℍ) where T<:RealOrComplex
(2) invsqrt(D{S}::𝔻) where S<:Real
```

正定な `Hermitian` 行列 $P$ の主平方根の逆数 $P^{-1/2}$ を計算します。

$$
P
$$

は Hermitian としてフラグ付けされる必要があります。行列の [型キャスティング](@ref) を参照してください。

実数の `Diagonal` 行列 (2) に対して特別なメソッドが提供されています。

### 数学

正定な行列 $P$ の主平方根は、唯一の対称（$P$ が実数の場合）または Hermitian（$P$ が複素数の場合）平方根です。その逆数 $P^{-1/2}$ は **ホワイトニング** または **スフィアリング** 行列とも呼ばれ、$P^{-1/2}PP^{-1/2}=I$ となります。

**参照**: [型キャスティング行列](@ref)。

**関連**: [`pow`](@ref)。

**例**

```julia
using LinearAlgebra, PosDefManifold
P=randP(ComplexF64, 5);
Q=invsqrt(P);
Q*P*Q ≈ I ? println(" ⭐ ") : println(" ⛔ ")
```
