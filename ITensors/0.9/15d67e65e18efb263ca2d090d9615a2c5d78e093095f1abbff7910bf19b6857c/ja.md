```
uniqueind(A, B; kwargs...)
```

`A`のインデックスの集合に固有であり、`B`には含まれない最初の`Index`を返します。

関連情報として[`uniqueinds`](@ref)を参照してください。

オプションのキーワード引数：

  * tags::String - 返されるインデックスがすべて持つ必要があるタグ名またはカンマ区切りのタグ名のリスト
  * plev::Int - 返されるインデックスがすべて持つ必要がある共通の素数レベル
  * inds - インデックスまたはインデックスのコレクション。返されるインデックスはこのインデックスの集合から来る必要があります。
