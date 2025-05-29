```
meanfinite([f=identity], A; kwargs...)
```

非有限値を無視しながら `mean(f, A)` を計算します。

サポートされている `kwargs` は `sum(f, A; kwargs...)` のものです。
