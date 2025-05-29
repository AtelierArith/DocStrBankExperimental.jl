```
CladoTree <: AbstractTree

CladoTree() :: CladoTree
CladoTree(nodes::AbstractVector{CladoNode}) :: CladoTree
CladoTree(tree::CladoTree) :: CladoTree
CladoTree(tree::ChronoTree) :: CladoTree
```

クラドグラムまたは日付のない系統樹の型で、[`CladoNode`](@ref) インスタンスで構成され、根を持つと仮定されています。

引数なしで呼び出すと、コンストラクタは空の `CladoTree` を返します。

[`ChronoTree`](@ref) は、時間に関するすべての情報を削除することで `CladoTree` に変換できます。
