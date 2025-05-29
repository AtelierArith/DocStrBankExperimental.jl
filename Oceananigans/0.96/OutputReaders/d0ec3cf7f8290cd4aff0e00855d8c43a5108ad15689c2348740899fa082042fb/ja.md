```
FieldTimeSeries(path, name;
                backend = InMemory(),
                architecture = nothing,
                grid = nothing,
                location = nothing,
                boundary_conditions = UnspecifiedBoundaryConditions(),
                time_indexing = Linear(),
                iterations = nothing,
                times = nothing,
                reader_kw = Dict{Symbol, Any}())
```

`FieldTimeSeries`を返し、`path`にあるJLD2出力からフィールド`name`の時系列をロードします。

# キーワード引数

  * `backend`: データを4D配列にロードするための`InMemory()`、`FieldTimeSeries`にインデックスを付ける際にディスクから遅延ロードするための`OnDisk()`。
  * `grid`: ネイティブグリッドが正しくシリアライズされなかった場合にデータに関連付けるグリッド。
  * `iterations`: ロードするイテレーション。ファイル内で見つかったすべてのイテレーションがデフォルトです。
  * `times`: 記録された保存時間との近似浮動小数点比較を通じて決定されたロードする保存時間。デフォルトは`iterations`に関連付けられた時間です。`times`が指定されている場合は`iterations`よりも優先されます。
  * `reader_kw`: ファイルを開くときに使用するリーダー（現在はJLD2のみ）に渡すキーワード引数の名前付きタプルまたは辞書。
