```
pairwise!(r::AbstractMatrix, dist::PreMetric, a)
```

`pairwise!(dist, r, a)`と同じです。

!!! warning
    この代替構文は非推奨であり、今後のDistancs.jlのリリースで削除されるため、その使用は推奨されません。代わりに`pairwise!(dist, r, a)`を呼び出してください。

