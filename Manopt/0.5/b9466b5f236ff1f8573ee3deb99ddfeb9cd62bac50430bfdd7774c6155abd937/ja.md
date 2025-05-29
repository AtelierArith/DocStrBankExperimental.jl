```
DebugGradientChange()
```

勾配の変化量をデバッグします（[`AbstractManoptSolverState`](@ref) `o` の `get_gradient(o)` に保存されています）前回の反復中。一般的なケースについては、[`DebugEntryChange`](@ref) を参照してください。

# キーワードパラメータ

  * `storage=`[`StoreStateAction`](@ref)`( (:Gradient,) )`: 前のデータのアクションのストレージ
  * `prefix="Last Change:"`: デバッグ出力のプレフィックス（`format`を設定した場合は無視されます）
  * `io=stdout`: デバッグを出力するデフォルトストリーム。
  * `format="$prefix %f"`: 出力を印刷するためのフォーマット
