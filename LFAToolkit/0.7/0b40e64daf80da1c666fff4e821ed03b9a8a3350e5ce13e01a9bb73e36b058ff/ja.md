```julia
TensorH1UniformBasis(numbernodes1d, numberquadraturepoints1d, numbercomponents, dimension)
```

ガウス・ルジャンドル積分点を用いた均等間隔の点でのテンソル積基底

# 引数:

  * `numbernodes1d::Int`:             1次元の均等間隔のノードの数
  * `numberquadraturepoints1d::Int`:  1次元のガウス・ルジャンドル積分点の数
  * `numbercomponents::Int`:          コンポーネントの数
  * `dimension::Int`:                 基底の次元

# 戻り値:

  * 均等間隔のノード上のH1ラグランジュテンソル積基底オブジェクト

# 例:

```jldoctest
# 均等間隔のノード上のH1ラグランジュテンソル積基底を生成
basis = TensorH1UniformBasis(4, 3, 2, 1);

# 検証
println(basis)

# 出力

tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 3
    numbercomponents: 2
    dimension: 1
```
