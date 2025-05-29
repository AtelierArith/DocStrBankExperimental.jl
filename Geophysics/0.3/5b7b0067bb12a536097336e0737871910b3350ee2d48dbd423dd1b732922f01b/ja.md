```
radius(θ,P::Planet) = 1/sqrt((cos(θ)/semimajor(P,U))^2+(sin(θ)/semiminor(P,U))^2)
```

惑星 `Planet` のパラメータ化された `radius` は、地心緯度 `θ` 座標（m）に関して表されます。
