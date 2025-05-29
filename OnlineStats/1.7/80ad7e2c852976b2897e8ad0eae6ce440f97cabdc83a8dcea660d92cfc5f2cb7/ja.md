```
FitMvNormal(d)
```

`d`次元MvNormal分布のオンラインパラメータ推定（MLE）。

# 例

```
y = randn(100, 2)
o = fit!(FitMvNormal(2), eachrow(y))
```
