```
pairwise!(r::AbstractMatrix, dist::PreMetric, a::AbstractMatrix; dims)
```

`pairwise!(dist, r, a; dims)`と同じです。

```
!!! warning
この代替構文は非推奨であり、将来のリリースのDistances.jlから削除されるため、その使用は推奨されません。代わりに`pairwise!(dist, r, a; dims)`を呼び出してください。
```
