```
ImitationLoss <: AbstractLossLayer
```

一般的な模倣損失の形式

```
L(θ, t_true) = max_y {δ(y, t_true) + α θᵀ(y - y_true) - (Ω(y) - Ω(y_true))}
```

  * `δ` がゼロのとき、これは [`FenchelYoungLoss`](@ref) と同等です。
  * `Ω` がゼロのとき、これは [`StructuredSVMLoss`](@ref) と同等です。

注意: デフォルトでは、`t_true` はフィールド `y_true` を持つ名前付きタプルですが、[`get_y_true`](@ref) メソッドが実装されている任意のデータ構造にすることができます。

# フィールド

  * `aux_loss_maximizer`: 上記の問題でのargmaxを計算する `(θ, t_true, α)` の関数
  * `δ`: 基本損失関数
  * `Ω`: 正則化関数
  * `α::Float64`: デフォルト値が1.0のハイパーパラメータ
