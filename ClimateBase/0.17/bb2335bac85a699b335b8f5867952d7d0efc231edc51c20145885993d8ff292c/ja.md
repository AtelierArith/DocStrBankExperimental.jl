```
spaceagg(f, A::ClimArray, W = nothing)
```

関数 `f`（例：`mean, std`）を使用して、`A` のすべての利用可能な空間（すなわち、経度と緯度）にわたって `A` を集約し、`A` の各部分をその空間的面積で重み付けします。

`W` は追加の重みであり、各空間ポイントに重みを付けるためのものです。`W` は `A` と同じ空間情報を持つ `ClimArray` であるか、`A` とまったく同じ次元を持つ必要があります。
