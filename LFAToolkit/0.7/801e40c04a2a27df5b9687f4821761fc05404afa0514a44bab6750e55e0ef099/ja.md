```julia
TensorH1LagrangeHProlongationBasis(
    numbernodes1d,
    numbercomponents,
    dimension,
    numberfineelements1d,
)
```

ガウス・レジャンドル・ロバット点におけるテンソル積 h-延長基底

# 引数:

  * `numbernodes1d::Int`:         要素ごとの1次元のガウス・レジャンドル・ロバットノードの数
  * `numbercomponents::Int`:      コンポーネントの数
  * `dimension::Int`:             基底の次元
  * `numberfineelements1d::Int`:  細かいグリッド要素の数

# 戻り値:

  * H1 ラグランジュテンソル積 h-延長基底オブジェクト

# 例:

```jldoctest
# H1 ラグランジュテンソル積 h-延長基底を生成
basis = TensorH1LagrangeHProlongationBasis(4, 3, 2, 2);

# 検証
println(basis)

# 出力

tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 7
    numbercomponents: 3
    dimension: 2
```
