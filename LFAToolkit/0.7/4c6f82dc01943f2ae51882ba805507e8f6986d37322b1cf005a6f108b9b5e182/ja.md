```julia
Jacobi(operator)
```

有限要素演算子のためのジャコビ対角前処理器

# 引数:

  * `operator::Operator`:  前処理する有限要素演算子

# 戻り値:

  * ジャコビ前処理器オブジェクト

# 例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);
mass = GalleryOperator("mass", 4, 4, mesh);

# 前処理器
jacobi = Jacobi(mass);

# 検証
println(jacobi)
println(jacobi.operator)

# 出力

jacobi 前処理器
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
    量子重み

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
