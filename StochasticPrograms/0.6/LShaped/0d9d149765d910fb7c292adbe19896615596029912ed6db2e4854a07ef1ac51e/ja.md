```
LevelSet
```

L字型アルゴリズムにおけるレベルセット正則化を使用するためのファンクタオブジェクト。`LShaped.Optimizer`の`regularize`を通じて[`LV`](@ref)オブジェクトを供給するか、[`Regularizer`](@ref)属性を設定することで作成されます。

...

# パラメータ

  * `λ::AbstractFloat = 0.5`: レベル位置L = (1-λ)*θ + λ*Q̃を制御します。これは現在の下限と上限の凸結合です。
  * `penaltyterm::PenaltyTerm = Quadratic`: penaltytermのバリアントを指定します（[`Quadratic`](@ref）、[`InfNorm`](@ref)、[`ManhattanNorm`][@ref]）。

...
