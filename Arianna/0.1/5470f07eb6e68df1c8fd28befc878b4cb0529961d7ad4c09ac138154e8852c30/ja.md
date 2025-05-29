```
StoreTrajectories{F<:Format} <: AriannaAlgorithm
```

シミュレーション中にシステムの軌跡を保存するアルゴリズム。

# フィールド

  * `paths::Vector{String}`: 出力ファイルへのパス
  * `files::Vector{IOStream}`: 軌跡を書き込むためのファイルハンドル
  * `fmt::F`: 出力ファイルのフォーマットタイプ
  * `store_first::Bool`: 初期化時に軌跡を保存するかどうか
  * `store_last::Bool`: 終了時に軌跡を保存するかどうか
