```
smoothen(noisy::AbstractVector, b)
```

配列 `noisy` を長さ `b` のスライディングウィンドウで平均化することによって滑らかにし、`noisy` を周期的にラップします。`mean(noisy)` は保持されます。
