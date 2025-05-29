```julia
OperatorField(basis, evaluationmodes)
```

有限要素オペレータの入力または出力、基底と評価モードを持つ

# 引数:

  * `basis::AbstractBasis`:                           フィールドの有限要素基底
  * `evaluationmodes::AbstractArray{EvaluationMode`:  基底評価モードの配列; 注意: ガウス重みは別のオペレータフィールドにリストされる必要があります

# オプション引数:

  * `name::String`:  オペレータフィールドの名前

# 戻り値:

  * 有限要素オペレータフィールドオブジェクト

# 例:

```jldoctest
# 基底
basis = TensorH1LagrangeBasis(4, 3, 2, 1);

# ガウス重みフィールド、入力のみ
weightsfield =
    OperatorField(basis, [EvaluationMode.quadratureweights], "quadrature weights");

# 検証
println(weightsfield)

# 入力または出力フィールド
inputfield = OperatorField(
    basis,
    [EvaluationMode.interpolation, EvaluationMode.gradient],
    "gradient of weak form input",
);

# 検証
println(inputfield)

# 出力

operator field:
  name:
    quadrature weights 
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 3
    numbercomponents: 2
    dimension: 1
  evaluation mode:
    quadratureweights
operator field:
  name:
    gradient of weak form input
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 3
    numbercomponents: 2
    dimension: 1
  evaluation modes:
    interpolation
    gradient
```
