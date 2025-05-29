UDE（ユニバーサル微分方程式）のパラメータを保持する可変構造体。

```
UDEparameters{ADJ <: AbstractAdjointMethod} <: AbstractParameters
```

# フィールド

  * `sensealg::SciMLBase.AbstractAdjointSensitivityAlgorithm`: アジョイント感度分析に使用される感度アルゴリズム。
  * `optimization_method::String`: 使用される最適化手法。
  * `loss_type::String`: 使用される損失関数のタイプ。
  * `scale_loss::Bool`: 損失をスケーリングするかどうかを示すブール値。
  * `target::Symbol`: 最適化のためのターゲット変数。
