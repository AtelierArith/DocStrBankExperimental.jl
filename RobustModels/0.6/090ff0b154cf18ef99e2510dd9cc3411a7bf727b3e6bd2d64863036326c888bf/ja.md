```
MEstimator{L<:LossFunction} <: AbstractMEstimator
```

与えられた損失関数のためのM推定量。

M推定量は、損失関数を最小化することによって得られます：

$$
\hat{\mathbf{\beta}} = \underset{\mathbf{\beta}}{\textrm{argmin}} \sum_{i=1}^n \rho\left(\dfrac{r_i}{\hat{\sigma}}\right)
$$

残差 $\mathbf{r} = \mathbf{y} - \mathbf{X} \mathbf{\beta}$ とロバストスケール推定値 $\hat{\sigma}$ を用いて。

# フィールド

  * `loss`: ロバスト推定に使用される[`LossFunction`](@ref)。
