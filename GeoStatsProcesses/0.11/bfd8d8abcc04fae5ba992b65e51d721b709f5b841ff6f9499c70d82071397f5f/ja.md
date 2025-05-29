```
GaussianProcess(func, mean=0)
```

与えられた地質統計的 `func`ション（例：変動関数）と `mean` を持つガウス過程。

## 例

```julia
# 一変量過程
GaussianProcess(GaussianVariogram())
GaussianProcess(SphericalCovariance(), 0.5)

# 多変量過程
GaussianProcess(LinearTransiogram(), [0.5, 0.5])
```
