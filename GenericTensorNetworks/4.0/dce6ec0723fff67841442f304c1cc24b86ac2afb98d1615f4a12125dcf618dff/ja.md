```
ConfigsMin{K, BOUNDED, TREESTORAGE} <:AbstractProperty
ConfigsMin(K=Single; bounded=true, tree_storage=false)
```

最小-Kサイズの構成を見つけます。

  * 対応するデータ型は、`K`が`Single`の場合は逆[`CountingTropical`](@ref)`{Float64,<:ConfigEnumerator}`であり、`K`が整数の場合は逆[`TruncatedPoly`](@ref)`{K,<:ConfigEnumerator}`です。
  * 重み付き制約充足問題は、`K`が`Single`の場合のみサポートされています。

## キーワード引数

  * `bounded`がtrueの場合、中間構成を保存するための作業メモリを削減するためにバウンディングトリック（またはブール勾配）を使用します。
  * `tree_storage`がtrueの場合、構成を保存するためによりメモリ効率の良いツリー構造を使用します。
