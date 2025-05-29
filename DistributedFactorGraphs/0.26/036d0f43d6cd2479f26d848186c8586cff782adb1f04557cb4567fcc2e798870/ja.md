```julia
lsf(dfg; ...)
lsf(dfg, _)

```

特定のタイプの因子を因子グラフでリストします。例として、因子グラフ `dfg` のすべての Point2Point2 因子をリストします:     lsfWho(dfg, :Point2Point2)

ノート

  * `Vector{Symbol}` を返します。
