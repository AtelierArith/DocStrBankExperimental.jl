```
evd(S::Union{𝕄{T}, ℍ{T}}) where T<:RealOrComplex
```

与えられた正半定値行列 $S$ に対して、固有ベクトルを列に持つ行列 $U$ と対角に固有値を持つ行列 $Λ$ からなる2タプル $(Λ, U)$ を返します。これは、Julia の [eigen](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.eigen) 関数の出力で、$UΛU'=S$ 形式です。

`eigen` 関数に関しては、固有値と関連する固有ベクトルは固有値の増加値によってソートされます。

$$
S
$$

は実数または複素数であり、Julia によって `Hermitian` としてフラグ付けされる場合があります（この場合、**PosDefManifold** はそれが正定値であると仮定します）。

[行列の型変換](@ref)を参照してください。

**関連情報**: [`spectralFunctions`](@ref)。

**例**

```julia
using PosDefManifold
A=randn(3, 3);
S=A+A';
Λ, U=evd(S); # これは (Λ, U)=evd(P) と同等です
(U*Λ*U') ≈ S ? println(" ⭐ ") : println(" ⛔ ")
# => UΛU'=S, UΛ=SU, ΛU'=U'S
```
