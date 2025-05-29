```
pagerank(g::ADiGraph, α=0.85, n=100, ϵ = 1.0e-6)
```

グラフ `g` の[PageRank](https://en.wikipedia.org/wiki/PageRank)を計算します。異なる減衰係数（`α`）、反復回数（`n`）、および収束閾値（`ϵ`）を指定することもできます。`n` 回の反復内に収束しない場合、エラーが返されます。
