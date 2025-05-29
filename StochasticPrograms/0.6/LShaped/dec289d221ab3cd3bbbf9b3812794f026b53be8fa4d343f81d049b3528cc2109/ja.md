```
RegularizedDecomposition
```

L字型アルゴリズムで正則化分解正則化を使用するためのファンクタオブジェクト。`LShaped.Optimizer`の`regularize`を通じて[`RD`](@ref)オブジェクトを供給するか、[`Regularizer`](@ref)属性を設定することで作成されます。

...

# パラメータ

  * `σ::AbstractFloat = 1.0`: 正則化パラメータの初期値。現在の主要反復からの偏差の相対的なペナルティを制御します。
  * `σ̅::AbstractFloat = 4.0`: 正則化パラメータの最大値。
  * `σ̲::AbstractFloat = 0.5`: 正則化パラメータの最小値。
  * `log::Bool = true`: L字型手続きが標準出力にログされるかどうかを指定します。
  * `penaltyterm::PenaltyTerm = Quadratic`: ペナルティ項のバリアントを指定します（[`Quadratic`](@ref), [`InfNorm`](@ref), [`ManhattanNorm`][@ref]）。

...
