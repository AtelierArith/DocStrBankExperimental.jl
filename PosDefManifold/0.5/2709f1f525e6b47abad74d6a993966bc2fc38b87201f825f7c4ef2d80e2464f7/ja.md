```julia
    (1) distanceSqr(metric::Metric, P::ℍ{T}) where T<:RealOrComplex
    (2) distanceSqr(metric::Metric, P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
    (3) distanceSqr(metric::Metric, D::𝔻{S}) where S<:Real
    (4) distanceSqr(metric::Metric, D::𝔻{S}, E::𝔻{S}) where S<:Real
```

**エイリアス**: `distance²`

(1) 正定値行列 $P$ と単位行列との*距離の二乗*（または*発散*）$δ^2(P, I)$ を返します。詳細は [原点からの距離](@ref) を参照してください。

(2) 2つの正定値行列 $P$ と $Q$ の間の*距離の二乗*（または*発散*）$δ^2(P, Q)$ を返します。詳細は [距離](@ref) を参照してください。

いずれの場合も、距離関数 $δ$ は、[Metric::列挙型](@ref) の型の引数 `metric` によって誘導されます。

(1) の $P$ と (2) の $P$, $Q$ は、julia によって `Hermitian` としてフラグ付けされる必要があります。詳細は [行列の型変換](@ref) を参照してください。

(3) と (4) は、それぞれ実正定値 `Diagonal` 行列に対する (1) と (2) の特殊化されたメソッドです。詳細は [ℍVector 型](@ref) と [𝔻Vector 型](@ref) を参照してください。

**数学**

点 $P$ に対するサポートされているメトリックの*単位からの二乗距離*は次の通りです：

|   メトリック    | 単位からの二乗距離                                                         |
|:----------:|:----------------------------------------------------------------- |
|   ユークリッド   | $∥P-I∥^2$                                                         |
|  逆ユークリッド   | $∥P^{-1}-I∥^2$                                                    |
| チョーイユークリッド | $∥L_P-I∥^2$                                                       |
|  対数ユークリッド  | $∥\textrm{log}P∥^2$                                               |
|  対数コレスキー   | $∥S_P∥^2+∥\textrm{log}D_P∥^2$                                     |
|   フィッシャー   | $∥\textrm{log}P∥^2$                                               |
|  logdet0   | $\textrm{logdet}\frac{1}{2}(P+I) - \frac{1}{2}\textrm{logdet}(P)$ |
|   ジェフリー    | $\frac{1}{2}\textrm{tr}(P+P^{-1})-n$                              |
|  ボン・ノイマン   | $\frac{1}{2}\textrm{tr}(P\textrm{log}P-\textrm{log}P)$            |
|  ワッサースタイン  | $\textrm{tr}(P+I) -2\textrm{tr}(P^{1/2})$                         |

点 $P$ と $Q$ のサポートされているメトリックに対する*二乗距離*は次の通りです：

|   メトリック    | 二乗距離                                                                                  |
|:----------:|:------------------------------------------------------------------------------------- |
|   ユークリッド   | $∥P-Q∥^2$                                                                             |
|  逆ユークリッド   | $∥P^{-1}-Q^{-1}∥^2$                                                                   |
| チョーイユークリッド | $∥ L_P - L_Q ∥^2$                                                                     |
|  対数ユークリッド  | $∥\textrm{log}P-\textrm{log}Q∥^2$                                                     |
|  対数コレスキー   | $∥S_P-S_Q∥^2+∥\textrm{log}D_P-\textrm{log}D_Q∥^2$                                     |
|   フィッシャー   | $∥\textrm{log}(P^{-1/2}QP^{-1/2})∥^2$                                                 |
|  logdet0   | $\textrm{logdet}\frac{1}{2}(P+Q) - \frac{1}{2}\textrm{logdet}(PQ)$                    |
|   ジェフリー    | $\frac{1}{2}\textrm{tr}(Q^{-1}P+P^{-1}Q)-n$                                           |
|  ボン・ノイマン   | $\frac{1}{2}\textrm{tr}(P\textrm{log}P-P\textrm{log}Q+Q\textrm{log}Q-Q\textrm{log}P)$ |
|  ワッサースタイン  | $\textrm{tr}(P+Q) -2\textrm{tr}(P^{1/2}QP^{1/2})^{1/2}$                               |

**凡例:** $L_X$, $S_X$ および $D_X$ は、$X$ のコレスキー下三角行列、その厳密に下三角の部分および対角部分を表します（したがって、$S_X+D_X=L_X$,  $L_XL_X^*=X$）。

**関連情報**: [`distanceSqrMat`](@ref).

**例 (1)**

```julia
using PosDefManifold
P=randP(10)
d=distanceSqr(Wasserstein, P)
e=distanceSqr(Fisher, P)
metric=Metric(Int(logdet0)) # または metric=logdet0
s=string(metric) # 現在のメトリックを確認
f=distance²(metric, P) #エイリアス distance² を使用
```

**例 (2)**

```julia
using PosDefManifold
P=randP(10)
Q=randP(10)
d=distanceSqr(logEuclidean, P, Q)
e=distance²(Jeffrey, P, Q)
```
