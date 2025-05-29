```
StructuredSVMLoss <: AbstractLossLayer
```

構造化サポートベクターマシンに関連する損失で、次のように定義されます。

```
L(θ, y_true) = max_y {δ(y, y_true) + α θᵀ(y - y_true)}
```

参考文献: [http://www.nowozin.net/sebastian/papers/nowozin2011structured-tutorial.pdf](http://www.nowozin.net/sebastian/papers/nowozin2011structured-tutorial.pdf) (第6章)

# フィールド

  * `aux_loss_maximizer::M`: 上記の問題でargmaxを計算する関数 `(θ, y_true, α)`
  * `δ::L`: 基本損失関数
  * `α::Float64`: デフォルト値1.0のハイパーパラメータ
