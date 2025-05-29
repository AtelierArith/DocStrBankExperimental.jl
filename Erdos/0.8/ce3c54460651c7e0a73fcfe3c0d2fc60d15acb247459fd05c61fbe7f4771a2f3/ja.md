```
egonet(g, v::Int, d::Int; dir=:out)
```

`g`によって誘導される`v`の隣接点のサブグラフを距離`d`まで返します。`g`が`DiGraph`の場合、`dir`オプション引数は`v`に対するエッジの方向（すなわち、考慮される方向は`:in`または`:out`）を指定します。これは、[`subgraph`](@ref)`(g, neighborhood(g, v, d, dir=dir))[1]`と同等です。
