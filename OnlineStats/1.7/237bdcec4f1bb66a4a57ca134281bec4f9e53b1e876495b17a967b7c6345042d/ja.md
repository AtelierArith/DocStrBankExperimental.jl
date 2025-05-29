```
FitLogNormal()
```

対数正規分布のオンラインパラメータ推定（最尤推定）。

# 例

```
o = fit!(FitLogNormal(), exp.(randn(10^5)))
```
