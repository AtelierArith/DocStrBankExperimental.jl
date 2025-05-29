```
paczynski(u) -> amplification
```

### 目的

単一の点状レンズによる点状ソースの重力マイクロレンズ増幅を計算します。

### 説明

Paczyńskiの公式を使用して、単一の点状レンズによる点状ソースの[重力マイクロレンズ](https://en.wikipedia.org/wiki/Gravitational_microlensing)増幅を返します。

$$
A(u) = \frac{u^2 + 2}{u\sqrt{u^2 + 4}}
$$

ここで、$u$はレンズとソースの間の投影距離を[アインシュタイン半径](https://en.wikipedia.org/wiki/Einstein_radius)の単位で表したものです。

$$
u
$$

の極端な値の計算を高速化するために、次の漸近的な表現が$A(u)$に使用されます：

$$
A(u) =
\begin{cases}
 1/u & |u| ≪ 1 \\
 \text{sgn}(u) & |u| ≫ 1
\end{cases}
$$

### 引数

  * `u`: レンズとソースの間の投影距離、アインシュタイン半径の単位で

### 出力

与えられた距離に対するマイクロレンズ増幅。

### 例

$$
u = 10^{-10}, 10^{-1}, 1, 10, 10^{10}
$$

のマイクロレンズ増幅を計算します：

```jldoctest
julia> paczynski.([1e-10, 1e-1, 1, 10, 1e10])
5-element Vector{Float64}:
  1.0e10
 10.037461005722337
  1.3416407864998738
  1.0001922892047386
  1.0
```

### 注記

マイクロレンズ増幅の$A(u)$の表現は、Bohdan Paczyńskiによって次のように示されました：

  * Paczynski, B. 1986, ApJ, 304, 1. DOI:[10.1086/164140](http://dx.doi.org/10.1086/164140), Bibcode:[1986ApJ...304....1P](http://adsabs.harvard.edu/abs/1986ApJ...304....1P)

同じ表現は、実際には半世紀前にAlbert Einsteinによって発見されました：

  * Einstein, A. 1936, Science, 84, 506. DOI:[10.1126/science.84.2188.506](http://dx.doi.org/10.1126/science.84.2188.506), Bibcode:[1936Sci....84..506E](http://adsabs.harvard.edu/abs/1936Sci....84..506E)
