```julia
DirichletBDDC(operator)
```

有限要素演算子のためのDirichlet BDDC前処理器

# 引数:

  * `operator::Operator`:  前処理する有限要素演算子

# 戻り値:

  * Dirichlet BDDC前処理器オブジェクト

# 例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);

# 演算子
finediffusion = GalleryOperator("diffusion", 5, 5, mesh);

# 前処理器
bddc = DirichletBDDC(finediffusion);

# 検証
println(bddc)
println(bddc.operator)

# 出力

Dirichlet BDDC前処理器
有限要素演算子:
2dメッシュ:
    dx: 1.0
    dy: 1.0

2つの入力:
演算子フィールド:
  テンソル積基底:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  評価モード:
    勾配
演算子フィールド:
  テンソル積基底:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  評価モード:
    積分重み

1つの出力:
演算子フィールド:
  テンソル積基底:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  評価モード:
    勾配
```
