```
pagerank(g, α=0.85, n=100, ϵ=1.0e-6)
```

グラフ `g` の[PageRank](https://en.wikipedia.org/wiki/PageRank)を、減衰係数 `α`、反復回数 `n`、および収束閾値 `ϵ` によってパラメータ化して計算します。`g` の各ノードに対して計算された中心性を表すベクトルを返すか、`n` 回の反復内に収束しなかった場合はエラーを返します。
