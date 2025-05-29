```
DebugGradientChange()
```

勾配の変化量をデバッグします（[`AbstractManoptSolverState`](@ref) `o` の `get_gradient(o)` に保存されている）前回の反復中に。一般的なケースについては、[`DebugEntryChange`](@ref) を参照してください。

# キーワードパラメータ

  * `storage`: （`StoreStateAction( (:Gradient,) )`）以前のデータのアクションのストレージ
  * `prefix`:  （`"Last Change:"`）デバッグ出力のプレフィックス（`format` を設定した場合は無視されます）
  * `io`:      （`stdout`）デバッグを出力するためのデフォルトストリーム。
  * `format`:  （`"$prefix %f"`）出力を印刷するためのフォーマット
