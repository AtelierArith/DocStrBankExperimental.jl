```
SEstimator{L<:BoundedLossFunction} <: AbstractMEstimator
```

与えられたバウンデッドロス関数のためのS推定量。

S推定量はスケール推定量を最小化することによって得られます：

$$
\hat{\mathbf{\beta}} = \underset{\mathbf{\beta}}{\textrm{argmin }} \hat{\sigma}^2
$$

ここで、ロバストスケール推定量 $\hat{\sigma}$ は次の方程式の解です：

$$
\dfrac{1}{n} \sum_{i=1}^n \rho\left(\dfrac{r_i}{\hat{\sigma}}\right) = \delta
$$

残差 $\mathbf{r} = \mathbf{y} - \mathbf{X} \mathbf{\beta}$ に対して、$\rho$ はバウンデッドロス関数であり、 $\underset{r \to \infty}{\lim} \rho(r) = 1$ であり、$\delta$ は有限のブレイクダウンポイントで、通常は0.5です。

# フィールド

  * `loss`: ロバスト推定に使用される [`LossFunction`](@ref) 。
