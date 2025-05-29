```
latitudegeodetic(θ,P::Planet) = atan(tan(θ)/(1-flattening(P))^2)
```

地心緯度 `θ` を `Planet` の表面での測地緯度に変換します（ラジアン）。
