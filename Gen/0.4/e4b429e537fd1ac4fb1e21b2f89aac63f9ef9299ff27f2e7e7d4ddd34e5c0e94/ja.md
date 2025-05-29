```
piecewise_uniform(bounds, probs)
```

区分的均一連続分布から `Float64` 値をサンプリングします。

`n` 個のビンがあり、`n = length(probs)` であり、`n + 1 = length(bounds)` です。境界はすべての `i` に対して `bounds[i] < bounds[i+1]` を満たす必要があります。`x` における確率密度は、`x <= bounds[1]` または `x >= bounds[end]` の場合はゼロであり、それ以外の場合は `probs[bin] / (bounds[bin] - bounds[bin+1])` であり、ここで `bounds[bin] < x <= bounds[bin+1]` です。
