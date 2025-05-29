```
latitudeparametric(ϕ,P::Planet) = atan(tan(ϕ)*(1-flattening(P)))
```

測地線緯度 `ϕ` を周囲の球体上のパラメトリック緯度に変換します（ラジアン）。
