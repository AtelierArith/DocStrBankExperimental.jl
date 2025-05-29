```
scaled_distance(D::ActionDistribution, x)
```

平均 $μ$ がサンプル多様体 $M$ 上にあり、共分散 $Σ$ が群 $G$ のリー代数 $\mathfrak{g}$ にある `ActionDistribution(μ,Σ)` 分布から始めます。群 $G$ の多様体 $M$ に対する無限小作用は、線形写像 $P \colon \mathfrak{g} \to T_{μ}M$ を生じ、これにより接空間 $T_{μ}M$ 上の投影共分散 $PΣP^*$ が得られます。

次に、次の式を用いて $v := \log(μ, x)$ から $μ$ から $x$ までのスケール距離を測定します。

$$
\frac{\sqrt{v^T (PΣP^*)^{-1} v}}{\sqrt{n}}
$$

（ここで $v$ は列行列として扱われ）、$n$ はサンプル多様体 $M$ の次元です。
