```
ChronoTree <: AbstractTree

ChronoTree(nodes::AbstractVector{ChronoNode}) :: ChronoTree
ChronoTree() :: ChronoTree
```

年代樹または日付付き系統樹の型で、根を持つと仮定され、[`ChronoNode`](@ref) インスタンスで構成されています。 [`CladoTree`](@ref) と比較してください。

引数なしで呼び出すと、コンストラクタは空の `ChronoTree` を返します。
