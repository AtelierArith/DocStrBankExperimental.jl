```
AccumulatedSeries{T}(::String = "")  (default T == Float64)
AccumulatedSeries{T}(::String = "", [::Int])  (default T == Float64)
```

[`MonteCarloMeasurement`](@ref) の一種で、[`OnlineLogBinning.jl`](https://meese-wj.github.io/OnlineLogBinning.jl/stable/) によって提供される *オンライン* ビニング分析を行いながら、特定の可観測量の統計を蓄積します。

!!! note
    *事前に割り当てられた* [`AccumulatedSeries`](@ref) は、最初の引数として `String` を、2 番目の引数として予想されるデータストリームの長さを示す `Int` 型の整数を取ります。

