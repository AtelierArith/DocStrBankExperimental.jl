```
pairwise!(r::AbstractMatrix, dist::PreMetric, a::AbstractMatrix, b::AbstractMatrix; dims)
```

`pairwise!(dist, r, a, b; dims)`と同じです。

!!! warning
    この代替構文は非推奨であり、今後のDistancess.jlのリリースで削除される予定です。その使用は推奨されません。代わりに`pairwise!(dist, r, a, b; dims)`を呼び出してください。

