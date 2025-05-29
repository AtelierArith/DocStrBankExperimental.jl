```
(l::NurbsLocator)(x,t)
```

NURBSのスプラインセグメントをループして、パラメータ値 `u⁺ = argmin_u (x-curve(u,t))²` を推定します。
