```
latitudegeocentric(ϕ,P::Planet) = atan(tan(ϕ)*(1-flattening(P))^2)
```

地理緯度 `ϕ` を `Planet` の表面での地心緯度に変換します（ラジアン）。
