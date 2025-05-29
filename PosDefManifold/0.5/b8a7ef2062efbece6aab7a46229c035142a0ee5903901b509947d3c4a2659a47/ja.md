```
frf(P::ℍ{T}) where T<:RealOrComplex
```

`P`のフルランク因子分解。次のように与えられます。

$$
F=UD^{1/2}
$$

,

ここで

$$
\textrm{EVD}(P)=UDU^{H}
$$

は`P`の固有値-固有ベクトル分解です。これは次のことを確認します。

$$
FF^H=P
$$

,

したがって$F^{-1}$はホワイトニング行列です。

**関連情報**: [`invfrf`](@ref).

**例**

```julia
using LinearAlgebra, PosDefManifold
P=randP(3)
F = frf(P)
F*F'≈P ? println(" ⭐ ") : println(" ⛔ ")
```
