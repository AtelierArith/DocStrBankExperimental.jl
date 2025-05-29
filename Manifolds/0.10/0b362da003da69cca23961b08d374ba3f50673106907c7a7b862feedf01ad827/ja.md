```
change_representer(M::PositiveNumbers, E::EuclideanMetric, p, X)
```

接触ベクトル $X ∈ T_p\mathcal M$ が [`EuclideanMetric`](@extref `ManifoldsBase.EuclideanMetric`) `g_E` に関して線形関数を表すとき、この関数は [`PositiveNumbers`](@ref) `M` の正の計量表現に関して表現者を変更します。

すべての接触ベクトル $Y$ に対して、結果 $Z$ は次の条件を満たさなければなりません。

$$
    ⟨X,Y⟩ = XY = \frac{ZY}{p^2} = g_p(YZ)
$$

したがって、$Z = p^2X$ です。
