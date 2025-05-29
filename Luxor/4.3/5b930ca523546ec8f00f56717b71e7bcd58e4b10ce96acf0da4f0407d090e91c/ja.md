```
mask(point::Point, focus::Point, radius)
    max = 1.0,
    min = 0.0,
    easingfunction = easingflat)
```

`focus`と`radius`で定義された円形領域に対して、`point`に相対的な0から1の値を計算します。この値は、円形領域の中心で`max`（1.0）に近づき、円周で`min`（0.0）に近づきます。
