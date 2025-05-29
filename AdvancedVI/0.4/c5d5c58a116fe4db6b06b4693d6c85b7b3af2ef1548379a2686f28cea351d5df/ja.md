```
MvLocationScale(location, scale, dist)
```

ロケーションスケール変分ファミリーは、`location` と `scale` 変分パラメータを使用して、さまざまな変分ファミリーを広く表現します。

一般的に、サンプリングパスが次のように表現できる任意の分布を表します：

```julia
  d = length(location)
  u = rand(dist, d)
  z = scale*u + location
```
