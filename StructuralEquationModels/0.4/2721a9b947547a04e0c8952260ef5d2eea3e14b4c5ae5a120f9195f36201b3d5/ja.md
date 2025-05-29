```
SemLoss(args...; loss_weights = nothing, ...)
```

SEMの損失フィールドを構築します。複数の`SemLossFunction`を含むことができ、モデルはそれらの合計に対して最適化されます。詳細は[`SemLossFunction`](@ref)を参照してください。

# 引数

  * `args...`: 複数の`SemLossFunction`。
  * `loss_weights::Vector`: 各損失関数の重み。デフォルトでは重みなしの最適化です。

# 例

```julia
my_ml_loss = SemML(...)
my_ridge_loss = SemRidge(...)
my_loss = SemLoss(SemML, SemRidge; loss_weights = [1.0, 2.0])
```
