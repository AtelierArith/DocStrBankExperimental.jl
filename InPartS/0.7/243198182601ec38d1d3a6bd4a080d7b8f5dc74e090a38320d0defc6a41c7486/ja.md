```
BinaryDumpCallback(trigger::AbstractCallback, filename)
```

コールバックは、Julia シリアライザーを使用して [`DynamicState`](@ref) を `filename` のバイナリ出力ファイルにダンプします。中間ファイルは、`trigger` コールバックがトリガーされるたびに [`prepropagate!`](@ref) で書き込まれ、最終ファイルは [`finalize!`](@ref) または [`freeze!`](@ref) で書き込まれます。

データの長期保存には意図されていません（代わりに [`SaveCallback`](@ref) を使用してください）。
