# TreeOfLife.jl

[![Documentation](https://img.shields.io/badge/docs-stable-blue.svg)](https://Mikumikunisiteageru.github.io/TreeOfLife.jl/stable) [![Documentation](https://img.shields.io/badge/docs-dev-blue.svg)](https://Mikumikunisiteageru.github.io/TreeOfLife.jl/dev) [![CI](https://github.com/Mikumikunisiteageru/TreeOfLife.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/Mikumikunisiteageru/TreeOfLife.jl/actions/workflows/CI.yml) [![Codecov](https://codecov.io/gh/Mikumikunisiteageru/TreeOfLife.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/Mikumikunisiteageru/TreeOfLife.jl) [![Aqua.jl Quality Assurance](https://img.shields.io/badge/Aquajl-%F0%9F%8C%A2-aqua.svg)](https://github.com/JuliaTesting/Aqua.jl)

TreeOfLife.jlは、系統学における系統樹と年代樹のデータ型を定義し、これらの木を分析するためのメソッドを提供します。

開発中です。

代替パッケージには以下が含まれます：

  * [Phylo.jl](https://github.com/EcoJulia/Phylo.jl)（「ベータ版」、およびその古いプロトタイプ [Phylogenetics.jl](https://github.com/SabrinaJaye/Phylogenetics.jl)）
  * [PhyloTrees.jl](https://github.com/jangevaare/PhyloTrees.jl)
  * [TreeTools.jl](https://github.com/PierreBarrat/TreeTools.jl)
  * [Phylogenies.jl](https://github.com/BioJulia/Phylogenies.jl)（「開発中」）

## 例

以下は、このパッケージの使用法を示すいくつかの簡単な例です。TreeOfLife.jlの詳細については、[ドキュメント](https://Mikumikunisiteageru.github.io/TreeOfLife.jl/)をご覧ください。

```julia
julia> using TreeOfLife

julia> tree = fromnewick("(A:0.1,B:0.2,(C:0.3,D:0.4)E:0.5)F;")
ChronoTree(ChronoNode[ChronoNode("F", 0, 0, 2, 0.0, 0.0), ChronoNode("A", 1, 3, 0, 0.1, 0.1), ChronoNode("B", 1, 4, 0, 0.2, 0.2), ChronoNode("E", 1, 0, 5, 0.5, 0.5), ChronoNode("C", 4, 6, 0, 0.8, 0.3), ChronoNode("D", 4, 0, 0, 0.9, 0.4)])

julia> tonewick(tree)
"(A:0.1,B:0.2,(C:0.3,D:0.4)E:0.5)F;"

julia> tipnames = gettipnames(tree)
4-element Vector{String}:
 "A"
 "B"
 "C"
 "D"

julia> getmrca(tree, tipnames)
1

julia> phylodiv(tree, tipnames)
1.5

julia> ismonophyl(tree, ["A", "B"])
false

julia> ismonophyl(tree, ["C", "D"])
true
```
