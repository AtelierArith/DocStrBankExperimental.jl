```
UDEparameters(; sensealg, optim_autoAD, grad, optimization_method, loss_type, empirical_loss_function, scale_loss, target) where {ADJ <: AbstractAdjointMethod}
```

`UDEparameters`オブジェクトを作成して、ユニバーサル微分方程式（UDE）の感度分析と最適化を構成します。

# キーワード引数

  * `sensealg::SciMLBase.AbstractAdjointSensitivityAlgorithm`: アジョイント計算に使用する感度アルゴリズム。デフォルトは`GaussAdjoint(autojacvec=SciMLSensitivity.EnzymeVJP())`です。
  * `optim_autoAD::AbstractADType`: 最適化のための自動微分タイプ。デフォルトは`Optimization.AutoEnzyme()`です。
  * `grad::ADJ`: アジョイント勾配計算メソッド。デフォルトは`SciMLSensitivityAdjoint()`です。
  * `optimization_method::String`: 使用する最適化メソッド。`"AD+AD"`または`"AD+Diff"`のいずれかでなければなりません。デフォルトは`"AD+AD"`です。
  * `loss_type::String`: 使用する損失関数のタイプ。`"V"`（速度）または`"H"`（厚さ）のいずれかでなければなりません。デフォルトは`"V"`です。
  * `empirical_loss_function::AbstractLoss`: 最適化に使用する損失関数。デフォルトは`L2Sum()`です。
  * `scale_loss::Bool`: 損失関数をスケーリングするかどうか。デフォルトは`true`です。
  * `target::Union{Symbol, Nothing}`: 最適化のためのターゲット変数。デフォルトは`:A`です。

# 戻り値

  * 指定された感度、最適化、および損失設定で構成された`UDEparameters`オブジェクト。

# 説明

この関数は、ユニバーサル微分方程式（UDE）フレームワークにおける感度分析、最適化、および損失計算の構成をカプセル化する`UDEparameters`オブジェクトを作成します。提供された`optimization_method`と`loss_type`が有効であることを確認し、それに応じてソルバーパラメータを構築します。

# 注意事項

  * `optimization_method`は、`"AD+AD"`（前方および後方パスの両方に対する自動微分）または`"AD+Diff"`（有限差分と組み合わせた自動微分）のいずれかでなければなりません。
  * `loss_type`は、`"V"`（速度ベースの損失）または`"H"`（厚さベースの損失）のいずれかでなければなりません。
  * `empirical_loss_function`は、最適化中に損失がどのように計算されるかを決定します。
