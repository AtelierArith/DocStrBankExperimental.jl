```
CalibrationProblem{P, M, A, Accessor, I, Q}
```

`BasketPricingProblem`をラップし、どの市場パラメータをAccessors.jlアクセスパスを使用してキャリブレーションするかを定義します。

# フィールド

  * `pricing_problem::BasketPricingProblem{P, M}`: ペイオフのバスケットと共有市場入力。
  * `pricing_method::A`: 使用される価格設定方法（例：ブラック-ショールズ）。
  * `accessors::Vector{Accessor}`: キャリブレーションするパラメータを指定する`Accessors.jl`レンズのリスト。
  * `quotes::Vector{Q}`: 一致させる観測市場価格。
  * `initial_guess::Vector{I}`: 各キャリブレーションされたパラメータの初期推測。
