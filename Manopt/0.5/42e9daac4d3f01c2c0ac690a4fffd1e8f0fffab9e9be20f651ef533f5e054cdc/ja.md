```
DebugChange(M=DefaultManifold(); kwargs...)
```

最後の反復中に、反復の変化量（[`AbstractManoptSolverState`](@ref)の`get_iterate(o)`に保存されている）をデバッグします。一般的なケースについては、[`DebugEntryChange`](@ref)を参照してください。

# キーワードパラメータ

  * `storage=`[`StoreStateAction`](@ref)`( [:Gradient] )` 前のアクションの保存
  * `prefix="Last Change:"`: デバッグ出力のプレフィックス（`format`を設定した場合は無視されます）
  * `io=stdout`: デバッグを出力するためのデフォルトストリーム。
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆再traction $\operatorname{retr}^{-1}$、再tractionとその逆に関するセクションを参照してください。[再traction](@extref ManifoldsBase :doc:`retractions`)

距離を近似するために使用される逆再traction。
