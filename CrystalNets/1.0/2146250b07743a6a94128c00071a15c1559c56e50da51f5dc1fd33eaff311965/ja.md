```
topological_genome(g::Union{String,PeriodicGraph}, options::Options=Options())
topological_genome(g::Union{String,PeriodicGraph}; kwargs...)
```

周期グラフのトポロジカルゲノムを計算します。トポロジカルキー（文字列として）を指定した場合、最初に`PeriodicGraph`に変換されます。

[`TopologicalGenome`](@ref)を返します。
