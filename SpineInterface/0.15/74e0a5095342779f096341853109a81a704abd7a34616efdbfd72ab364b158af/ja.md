```
using_spinedb(url::String, mod=@__MODULE__; upgrade=false, filters=Dict(), extend=false)
```

モジュール `mod` を拡張して、Spine DB の内容にアクセスするための便利な関数を提供します。引数 `url` は、DB の URL またはそれに関連付けられた HTTP Spine DB サーバーの URL です。

# キーワード引数

  * `upgrade`: `true` の場合、データベースは最新のリビジョンにアップグレードされます。
  * `filters`: フィルターを指定する `Dict` です。
  * `extend`: `false` の場合、指定されたモジュール内で既に作成された便利な関数は上書きされます。そうでなければ、それらは拡張されます。

便利なファンクタを呼び出す方法の詳細については、[`ObjectClass()`](@ref)、[`RelationshipClass()`](@ref)、および [`Parameter()`](@ref) を参照してください。
