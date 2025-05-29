```
StoreLastFrames <: AriannaAlgorithm
```

シミュレーションの終了時に各システムの最終状態を保存するアルゴリズムです。

# フィールド

  * `paths::Vector{String}`: 出力ファイルへのパス
  * `fmt::Format`: 出力ファイルのフォーマットタイプ
