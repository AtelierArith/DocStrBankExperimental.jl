```julia
    (1) logMap(metric::Metric, P::ℍ{T}, G::ℍ{T})

    (2) logMap(metric::Metric, 𝐏::ℍVector, G::ℍ{T})
    すべての上記について: T<:RealOrComplex
```

(1) *対数マップ:* SPDまたはエルミート多様体から基準点$G$での接空間に、正定値行列$P$をマップします。[Fisher](@ref)メトリックを使用します。

$$
P
$$

と$G$は`Hermitian`としてフラグ付けされる必要があります。[行列の型変換](@ref)を参照してください。

このマップは次のように定義されます。

$$
Log_G(P)=S=G^{1/2}\textrm{log}\big(G^{-1/2}PG^{-1/2}\big)G^{1/2}
$$

。

`metric`は、[Metric::列挙型](@ref)のメトリックです。

結果は`Hermitian`行列です。

(2) *対数マップ* (1)で、基準点$G$で同時に$k$個の正定値行列を1次元配列$𝐏={P_1,...,P_k}$の[ℍVector型](@ref)として処理します。

結果は`ℍVector`です。

!!! note "Nota Bene"
    現在、接空間操作には[Fisher](@ref)メトリックのみがサポートされています。


逆操作は[`expMap`](@ref)です。

**関連項目**: [`vecP`](@ref), [`parallelTransport`](@ref).

**例**

```julia
using PosDefManifold
(1)
P=randP(3)
Q=randP(3)
metric=Fisher
G=mean(metric, P, Q)
# PをPとQの幾何平均によって与えられた基準点で投影します。
S=logMap(metric, P, G)

(2)
Pset=randP(3, 4)
# Pset内のすべての行列をそれらの幾何平均によって与えられた基準点で投影します。
Sset=logMap(Fisher, Pset, mean(Fisher, Pset))
```
