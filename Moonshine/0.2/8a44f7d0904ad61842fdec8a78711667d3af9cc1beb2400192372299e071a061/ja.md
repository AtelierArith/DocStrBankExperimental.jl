```julia
abstract type AbstractGenealogy <: Graphs.SimpleGraphs.AbstractSimpleGraph{Int32}
```

系譜のための抽象型。

[Graphs.jlインターフェース](https://juliagraphs.org/Graphs.jl/stable/ecosystem/interface/)を実装しているため、AbstractGenealogyインターフェースを実装するサブタイプは、通常のグラフとしても扱うことができます。

[Tree](@ref) と [Arg](@ref) は、AbstractGenealogyインターフェースを実装するサブタイプです。
