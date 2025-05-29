```julia
Hmultigrid(fineoperator, coarseoperator, smoother, prolongationbases)
```

H-Multigrid前処理器（有限要素演算子用）

# 引数:

  * `fineoperator::Operator`:                             前処理する有限要素演算子
  * `coarseoperator::Union{Operator,Multigrid}`:          前処理する有限要素演算子の粗いグリッド表現
  * `smoother::AbstractPreconditioner`:                   誤差緩和演算子（例：ヤコビ）
  * `prolongationbases::AbstractArray{<:AbstractBasis}`:  粗いグリッドから細いグリッドへの要素延長基底

# 戻り値:

  * h-multigrid前処理器オブジェクト

# 例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);
ctofbasis = TensorH1LagrangeHProlongationBasis(2, 1, 2, 2);

# 演算子
function diffusionweakform(du::Array{Float64}, w::Array{Float64})
    dv = du * w[1]
    return [dv]
end
# -- 細かい
basis = TensorH1LagrangeMacroBasis(2, 3, 1, 2, 2);
inputs = [
    OperatorField(basis, [EvaluationMode.gradient]),
    OperatorField(basis, [EvaluationMode.quadratureweights]),
];
outputs = [OperatorField(basis, [EvaluationMode.gradient])];
finediffusion = Operator(diffusionweakform, mesh, inputs, outputs);
# -- 粗い
basis = TensorH1LagrangeBasis(2, 3, 1, 2);
inputs = [
    OperatorField(basis, [EvaluationMode.gradient]),
    OperatorField(basis, [EvaluationMode.quadratureweights]),
];
outputs = [OperatorField(basis, [EvaluationMode.gradient])];
coarsediffusion = Operator(diffusionweakform, mesh, inputs, outputs);

# スムーザー
jacobi = Jacobi(finediffusion);

# 前処理器
multigrid = HMultigrid(finediffusion, coarsediffusion, jacobi, [ctofbasis]);

# 検証
println(multigrid)
println(multigrid.fineoperator)

# 出力

h-multigrid前処理器
有限要素演算子:
2dメッシュ:
    dx: 1.0
    dy: 1.0

2つの入力:
演算子フィールド:
  マクロ要素テンソル積基底:
    numbernodes1d: 3
    numberquadraturepoints1d: 6
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  評価モード:
    勾配
演算子フィールド:
  マクロ要素テンソル積基底:
    numbernodes1d: 3
    numberquadraturepoints1d: 6
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  評価モード:
    積分重み

1つの出力:
演算子フィールド:
  マクロ要素テンソル積基底:
    numbernodes1d: 3
    numberquadraturepoints1d: 6
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  評価モード:
    勾配
```
