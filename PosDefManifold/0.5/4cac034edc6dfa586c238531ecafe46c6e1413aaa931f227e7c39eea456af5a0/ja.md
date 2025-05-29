```julia
    (1) expMap(metric::Metric, S::ℍ{T}, G::ℍ{T})

    (2) expMap(metric::Metric, 𝐒::ℍVector, G::ℍ{T})
    上記すべてについて: ここで T<:RealOrComplex
```

(1) *指数写像:* 接ベクトル（行列）$S$を基準点$G$での接空間からSPDまたはエルミート多様体に写像します（[Fisher](@ref) メトリックを使用）。

$$
S
$$

と$G$は`Hermitian`としてフラグ付けされる必要があります。[行列の型キャスティング](@ref)を参照してください。

写像は次のように定義されます。

$$
Exp_G(S)=P=G^{1/2}\textrm{exp}\big(G^{-1/2}SG^{-1/2}\big)G^{1/2}
$$

。

`metric`は[Metric::列挙型](@ref)のメトリックです。

結果は`Hermitian`行列です。

(2) *指数写像* (1)を基準点$G$で同時に$k$個の接ベクトル（行列）を1次元配列$𝐒={S_1,...,S_k}$の[ℍVector型](@ref)で処理します。

結果は`ℍVector`です。

!!! note "Nota Bene"
    現在、接空間操作には[フィッシャー](@ref)メトリックのみがサポートされています。


逆操作は[`logMap`](@ref)です。

**例**

```julia
(1)
using PosDefManifold, LinearAlgebra
P=randP(3)
Q=randP(3)
G=mean(Fisher, P, Q)
# フィッシャー平均基準点Gでの接空間にPを投影
S=logMap(Fisher, P, G)
# 多様体に戻す
P2=expMap(Fisher, S, G)

(2)
Pset=randP(3, 4)
# 幾何平均によって与えられた基準点でPset内のすべての行列を投影
G=mean(Fisher, Pset)
Sset=logMap(Fisher, Pset, G)
# 多様体に戻す
Pset2=expMap(Fisher, Sset, G)
```
