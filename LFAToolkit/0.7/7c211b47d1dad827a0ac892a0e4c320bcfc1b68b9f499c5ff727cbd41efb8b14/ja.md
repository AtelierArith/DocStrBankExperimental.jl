```julia
Operator(weakform, mesh, inputs, outputs)
```

弱形式と基底から構成される有限要素演算子

# 引数:

  * `weakform::Function`:                     積分点での弱形式を表すユーザー提供関数
  * `mesh::Mesh`:                             各次元の変形を持つメッシュオブジェクト
  * `inputs::AbstractArray{OperatorField}`:   演算子入力フィールドの配列
  * `outputs::AbstractArray{OperatorField}`:  演算子出力フィールドの配列

# 戻り値:

  * 有限要素演算子オブジェクト

# 例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);
basis = TensorH1LagrangeBasis(4, 4, 1, 2);

function massweakform(u::Array{Float64}, w::Array{Float64})
    v = u * w[1]
    return [v]
end

# 質量演算子
inputs = [
    OperatorField(basis, [EvaluationMode.interpolation]),
    OperatorField(basis, [EvaluationMode.quadratureweights]),
];
outputs = [OperatorField(basis, [EvaluationMode.interpolation])];
mass = Operator(massweakform, mesh, inputs, outputs);

# 検証
println(mass)

# 出力

有限要素演算子:
2d メッシュ:
    dx: 1.0
    dy: 1.0

2 入力:
演算子フィールド:
  テンソル積基底:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  評価モード:
    補間
演算子フィールド:
  テンソル積基底:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  評価モード:
    積分重み

1 出力:
演算子フィールド:
  テンソル積基底:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  評価モード:
    補間
```
