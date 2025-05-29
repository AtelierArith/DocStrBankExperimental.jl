predict(m::RegularizedModel, newX::AbstractMatrix; kwargs...)

正則化パスの選択されたセグメントを使用した予測値。

# 例

```julia
m = fit(LassoModel, X, y; select=MinBIC())
predict(m, newX)     # BIC最小化セグメントを使用して予測
```
