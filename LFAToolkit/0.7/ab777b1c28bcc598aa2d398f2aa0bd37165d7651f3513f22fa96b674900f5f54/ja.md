```julia
TensorH1LagrangePProlongationBasis(
    numbercoarsenodes1d,
    numberfinenodes1d,
    numbercomponents,
    dimension,
)
```

ガウス・レジャンドル・ロバト点におけるテンソル積p-延長基底

# 引数:

  * `numbercoarsenodes1d::Int`:  1次元における粗いグリッドのガウス・レジャンドル・ロバトノードの数
  * `numberfinenodes1d::Int`:    1次元における細かいグリッドのガウス・レジャンドル・ロバトノードの数
  * `numbercomponents::Int`:     コンポーネントの数
  * `dimension::Int`:            基底の次元

# 戻り値:

  * H1ラグランジュテンソル積p-延長基底オブジェクト

# 例:

```jldoctest
# H1ラグランジュテンソル積p-延長基底を生成
basisctof = TensorH1LagrangePProlongationBasis(2, 3, 1, 2);

# 検証
println(basisctof)

# 出力

テンソル積基底:
    numbernodes1d: 2
    numberquadraturepoints1d: 3
    numbercomponents: 1
    dimension: 2
```
