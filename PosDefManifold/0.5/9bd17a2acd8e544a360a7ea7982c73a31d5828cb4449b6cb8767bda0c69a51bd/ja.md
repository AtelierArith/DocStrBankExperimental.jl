```
invfrf(P::ℍ{T}) where T<:RealOrComplex
```

行列 `P` のフルランク因子分解の逆行列です。次のように与えられます。

$$
F=D^{-1/2}U^H
$$

,

ここで

$$
\textrm{EVD}(P)=UDU^{H}
$$

は `P` の固有値-固有ベクトル分解です。これは次のことを確認します。

$$
FPF^H=I
$$

,

したがって $F$ はホワイトニング行列です。

**関連情報**: [`frf`](@ref).

**例**

```julia
using LinearAlgebra, PosDefManifold
P=randP(3)
F = invfrf(P)
F*P*F'≈I ? println(" ⭐ ") : println(" ⛔ ")
```
