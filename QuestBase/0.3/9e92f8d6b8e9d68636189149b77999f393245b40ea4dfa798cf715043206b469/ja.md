```julia
mutable struct HarmonicEquation
```

ハーモニクスを支配する代数方程式のセットを保持します。

# フィールド

  * `equations::Vector{Symbolics.Equation}`: ハーモニクスを支配する方程式のセット。
  * `variables::Vector{QuestBase.HarmonicVariable}`: ハーモニクスを記述する変数のセット。
  * `parameters::Vector{Symbolics.Num}`: 方程式セットのパラメータ。
  * `natural_equation::QuestBase.DifferentialEquation`: 自然方程式（ハーモニックアンサッツが使用される前）。
  * `jacobian::Matrix{Symbolics.Num}`: 自然方程式のヤコビ行列。
