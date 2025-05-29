```
ConfigsAll{TREESTORAGE} <:AbstractProperty
ConfigsAll(; tree_storage=false)
```

すべての有効な構成を見つけます。たとえば、[`IndependentSet`](@ref) 問題の場合、すべての独立した集合を見つけます。

  * 対応するデータ型は [`ConfigEnumerator`](@ref) です。
  * 重みは効果を持ちません。

## キーワード引数

  * `tree_storage` が true の場合、構成を格納するためによりメモリ効率の良い木構造を使用します。
