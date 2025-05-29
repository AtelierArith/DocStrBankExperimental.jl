```julia
    (1) parallelTransport(S::ℍ{T}, P::ℍ{T}, Q::ℍ{T})

    (2) parallelTransport(S::ℍ{T}, P::ℍ{T})

    (3) parallelTransport(𝐒::ℍVector, P::ℍ{T}, Q::ℍ{T})

    (4) parallelTransport(𝐒::ℍVector, P::ℍ{T})
    上記すべて: ここで T<:RealOrComplex
```

**エイリアス**: `pt`

(1) *平行輸送* は、基準点 $P$ での接空間にある接ベクトル $S$（行列）を基準点 $Q$ での接空間に輸送します。

$$
S
$$

, $P$ および $Q$ はすべて `Hermitian` 行列でなければなりません。`Hermitian` 行列を返します。輸送は次のように定義されます：

$$
∥_{(P→Q)}(S)=\big(QP^{-1}\big)^{1/2}S\big(QP^{-1}\big)^{H/2}
$$

。

もし $S$ が多様体内の正定値行列である場合（接ベクトルではなく）、それは $P$ から $Q$ に「輸送」され、次のようになります（Yair et *al.*, 2019[🎓](@ref)）

  * $$
    S
    $$

    を基準点 $P$ での接空間に射影する、
  * それを基準点 $Q$ での接空間に平行輸送する、
  * 基準点 $Q$ で多様体に戻す。

(2) (1) と同様の *平行輸送* ですが、基準点の *単位行列* での接空間に対して行います。

この場合、輸送は次のように簡略化されます：

$$
∥_{(P→I)}(S)=P^{-1/2}SP^{-1/2}
$$

。

(3) (1) と同様の *平行輸送* を、1次元配列 $𝐒={S_1,...,S_k}$ の $k$ 個の接ベクトル（行列）に対して一度に行います [ℍVector type](@ref)。

(4) (2) と同様の *平行輸送* を、1次元配列 $𝐒={S_1,...,S_k}$ の $k$ 個の接ベクトル（行列）に対して一度に行います [ℍVector type](@ref)。

!!! note "Nota Bene"
    現在、平行輸送には [Fisher](@ref) メトリックのみがサポートされています。


**関連項目**: [`logMap`](@ref), [`expMap`](@ref), [`vecP`](@ref), [`matP`](@ref)。

**例**

```julia
using PosDefManifold

(1)
P=randP(3)
Q=randP(3)
G=mean(Fisher, P, Q)

# i. 基準点 G での接空間に P を射影する
S=logMap(Fisher, P, G)
# ii. 接空間に S を平行輸送する基準点 Q で
S_=parallelTransport(S, G, Q)
# iii. 基準点 Q で多様体に戻す
P_=expMap(Fisher, S_, Q)

# i., ii. および iii. は単純に次のように行うことができます
PP_=parallelTransport(P, G, Q)
# チェック
P_≈PP_ ? println(" ⭐ ") : println(" ⛔ ")

(2)
P=randP(3)
Q=randP(3)
G=mean(Fisher, P, Q)
# 基準点の単位行列での接空間に輸送
PP_=parallelTransport(P, G)

(3)
Pset=randP(3, 4)
Q=randP(3)
G=mean(Fisher, Pset)
# Pset 内のすべての行列を一度に輸送
Pset2=parallelTransport(Pset, G, Q)

(4)
Pset=randP(3, 4)
G=mean(Fisher, Pset)
# 平均が I になるようにすべての行列を再中心化
Pset2=parallelTransport(Pset, G)
# チェック
mean(Fisher, Pset2) ≈ I ? println(" ⭐ ") : println(" ⛔ ")
```
