```
coef(path::RegularizationPath, select::SegSelect)
```

正則化パスの選択されたセグメントの係数ベクトル。

# 例

```julia
coef(path, MinBIC())     # BIC最小化セグメント
coef(path, AllSeg())     # パス全体の係数を含む配列
```
