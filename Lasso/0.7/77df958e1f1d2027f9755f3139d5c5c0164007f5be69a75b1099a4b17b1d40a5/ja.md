```
coef(path::RegularizationPath; kwargs...)
```

正則化パスの選択されたセグメントの係数ベクトル。

# 例

```julia
coef(path; select=MinBIC())     # BIC最小化セグメント
coef(path; select=AllSeg())     # パス全体の係数を含む配列
```
