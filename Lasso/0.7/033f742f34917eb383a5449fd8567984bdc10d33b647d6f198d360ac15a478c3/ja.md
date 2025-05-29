predict(path::RegularizationPath, newX::AbstractMatrix; kwargs...)

正則化パスの選択されたセグメントに対する予測値。

# 例

```julia
predict(path, newX; select=MinBIC())     # BIC最小化セグメントを使用して予測
```
