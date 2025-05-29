```
DebugChange(M=DefaultManifold())
```

最後の反復中に反復の変化量（[`AbstractManoptSolverState`](@ref)の`get_iterate(o)`に保存されている）をデバッグします。一般的なケースについては[`DebugEntryChange`](@ref)を参照してください。

# キーワードパラメータ

  * `storage`:                   （`StoreStateAction( [:Gradient] )`）前のアクションのストレージ
  * `prefix`:                    （`"Last Change:"`）デバッグ出力のプレフィックス（`format`を設定した場合は無視されます）
  * `io`:                        （`stdout`）デバッグを出力するためのデフォルトストリーム。
  * `format`:                    （`"$prefix %f"`）出力を印刷するためのフォーマット。
  * `inverse_retraction_method`: （`default_inverse_retraction_method(M)`）距離を近似するために使用される逆再引き戻し。
