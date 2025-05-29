```
colwise!(r::AbstractArray, dist::PreMetric, a, b)
```

`colwise!(dist, r, a, b)`と同じです。

!!! warning
    この代替構文は非推奨であり、将来のDistancias.jlのリリースで削除される予定です。その使用は推奨されません。代わりに`colwise!(dist, r, a, b)`を呼び出してください。

