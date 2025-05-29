```
FitGamma(; weight)
```

ガンマ分布のオンラインパラメータ推定（モーメント法）。

# 例

```
using Random
o = fit!(FitGamma(), randexp(10^5))
```
