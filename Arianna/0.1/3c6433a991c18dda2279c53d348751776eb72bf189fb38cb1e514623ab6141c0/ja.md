```
StoreBackups <: AriannaAlgorithm
```

シミュレーション中のシステム状態のバックアップファイルを作成するアルゴリズム。

# フィールド

  * `dirs::Vector{String}`: バックアップファイルを保存するディレクトリ
  * `fmt::Format`: 出力ファイルのフォーマットタイプ
  * `store_first::Bool`: 初期化時にバックアップを保存するかどうか
  * `store_last::Bool`: 終了時にバックアップを保存するかどうか
