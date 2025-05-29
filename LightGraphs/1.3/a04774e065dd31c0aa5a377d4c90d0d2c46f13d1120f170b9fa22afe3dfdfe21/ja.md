```
egonet(g, v, d, distmx=weights(g))
```

`g`によって誘導される部分グラフを返します `v`の隣接点までの距離 `d`、オプションで`distmx`によって提供される重みを使用します。これは、[`induced_subgraph`](@ref)`(g, neighborhood(g, v, d, dir=dir))[1]`と同等です。

### オプション引数

  * `dir=:out`: `g`が有向の場合、この引数は`v`に対するエッジの方向を指定します（すなわち、`:in`または`:out`）。
