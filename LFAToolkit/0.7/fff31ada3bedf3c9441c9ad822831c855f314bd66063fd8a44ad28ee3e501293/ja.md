```julia
Pmultigrid(fineoperator, coarseoperator, smoother, prolongationbases)
```

有限要素演算子のためのP-マルチグリッド前処理器

# 引数:

  * `fineoperator::Operator`:                             前処理する有限要素演算子
  * `coarseoperator::Union{Operator,Multigrid}`:          前処理する有限要素演算子の粗いグリッド表現
  * `smoother::AbstractPreconditioner`:                   誤差緩和演算子、例えばヤコビ
  * `prolongationbases::AbstractArray{<:AbstractBasis}`:  粗いグリッドから細いグリッドへの要素延長基底

# 戻り値:

  * p-マルチグリッド前処理器オブジェクト

# 例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);
ctofbasis = TensorH1LagrangePProlongationBasis(3, 5, 1, 2);

# 演算子
finediffusion = GalleryOperator("diffusion", 5, 5, mesh);
coarsediffusion = GalleryOperator("diffusion", 3, 5, mesh);

# スムーザー
jacobi = Jacobi(finediffusion);

# 前処理器
multigrid = PMultigrid(finediffusion, coarsediffusion, jacobi, [ctofbasis]);

# 検証
println(multigrid)
println(multigrid.fineoperator)

# 出力

p-マルチグリッド前処理器
有限要素演算子:
2d メッシュ:
    dx: 1.0
    dy: 1.0

2 入力:
演算子フィールド:
  テンソル積基底:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  評価モード:
    gradient
演算子フィールド:
  テンソル積基底:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  評価モード:
    quadratureweights

1 出力:
演算子フィールド:
  テンソル積基底:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  評価モード:
    gradient
```
