```
RobustAndOptimalControl.named_ss(sys::ModelingToolkit.AbstractTimeDependentSystem, inputs, outputs; descriptor=true, kwargs...)
```

線形化を使用して `ODESystem` を `NamedStateSpace` に変換します。`inputs, outputs` はそれぞれ入力と出力を決定する変数のベクトルです。`kwargs` に関する詳細は `ModelingToolkit.linearize` のドキュメントを参照してください。

`descriptor = true`（デフォルト）の場合、このメソッドはMTKが適切な形式を生成できなかったシステムを、ここで説明されている方法を使用して適切な線形状態空間システムに自動的に変換します: https://juliacontrol.github.io/ControlSystemsMTK.jl/dev/#Internals:-Transformation-of-non-proper-models-to-proper-statespace-form `descriptor = false` の場合、システムは代わりに `sys[:,uinds] + sys[:,duinds]*tf('s')` を使用して状態空間実現に変換され、ユーザーは慎重に選択した許容誤差で `minreal(sys, tol)` を呼び出すことを望むかもしれません。

また、内部で呼び出される低レベルの関数である [`ModelingToolkit.linearize`](@ref) も参照してください。関数 [`get_named_sensitivity`](@ref)、[`get_named_comp_sensitivity`](@ref)、[`get_named_looptransfer`](@ref) は、`named_ss` と同様に信号名を保持しながら感度関数を計算する便利な方法を提供します。対応する低レベルの関数 `get_sensitivity`、`get_comp_sensitivity` および `get_looptransfer` は ModelingToolkitStandardLibrary.Blocks にあり、[MTKstdlib: Linear analysis](https://docs.sciml.ai/ModelingToolkitStandardLibrary/stable/API/linear_analysis/) に文書化されています。 ```
