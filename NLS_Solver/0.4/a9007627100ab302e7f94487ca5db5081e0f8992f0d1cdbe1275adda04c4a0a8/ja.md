```julia
eval_r_J(nls::AbstractNLS,θ::AbstractVector) -> (r,J)
```

残差ベクトル $\mathbf{r}$ とそのヤコビ行列 $\mathbf{J}$ を計算します。
