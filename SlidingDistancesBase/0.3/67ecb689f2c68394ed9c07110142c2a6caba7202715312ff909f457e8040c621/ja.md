```
struct BatchSearchResult{T} <: AbstractSearchResult{T}
```

ベクトルのベクトルに対して検索を適用した後の結果を格納します。この型のインスタンス `bsr` は比較において数値として機能し、BatchSearchResult のベクトルは `value` に基づいてソートできます。`BatchSearchResult` はベクトルへのインデックスとしても機能します。インデックスされたベクトル `v` が `target` と同じ型である場合、`v` へのウィンドウが返されます。ベクトルが他のエレメンタイプである場合、`v[bsr.batch_ind]` が返されます。

アクセサ関数 [`value`](@ref), [`location`](@ref), [`payload`](@ref), [`target`](@ref), [`targetlength`](@ref) を参照してください。

# 引数:

  * `target`: 検索対象を含む
  * `value`: 見つかったものの値を含む（距離やコストなど）
  * `ind`: `value` が見つかった検索されたベクトルへのインデックス。
  * `batch_ind`: 外部ベクトル（またはファイルなど）のインデックス。
  * `payload`: 検索に関連する追加情報。
