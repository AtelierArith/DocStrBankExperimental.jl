```
ConfigsMax{K, BOUNDED, TREESTORAGE} <:AbstractProperty
ConfigsMax(K=Single; bounded=true, tree_storage=true)
```

最大Kサイズの構成を見つけます。たとえば、[`IndependentSet`](@ref)問題の場合、サイズが$\alpha(G), \alpha(G)-1, \ldots, \alpha(G)-K+1$のすべての独立集合を見つけることです。

  * 対応するデータ型は、`K`が`Single`の場合は[`CountingTropical`](@ref)`{Float64,<:ConfigEnumerator}`であり、`K`が整数の場合は[`TruncatedPoly`](@ref)`{K,<:ConfigEnumerator}`です。
  * 重み付き制約充足問題は、`K`が`Single`の場合のみサポートされています。

## キーワード引数

  * `bounded`がtrueの場合、中間構成を保存するための作業メモリを削減するためにバウンディングトリック（またはブール勾配）を使用します。
  * `tree_storage`がtrueの場合、構成を保存するためにメモリ効率の良いツリー構造を使用します。
