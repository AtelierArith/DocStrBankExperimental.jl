```julia
TensorBasis(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension,
    nodes1d,
    quadraturepoints1d,
    quadratureweights1d,
    interpolation1d,
    gradient1d;
    numberelements1d = 1,
)
```

テンソル積基底

# 引数:

  * `numbernodes1d`:             1次元のノード数
  * `numberquadraturepoints1d`:  1次元のガウス点数
  * `numbercomponents`:          コンポーネント数
  * `dimension`:                 基底の次元
  * `nodes1d`:                   1次元のノードの座標
  * `quadraturepoints1d`:        1次元のガウス点の座標
  * `quadratureweights1d`:       1次元のガウス重み
  * `interpolation1d`:           1次元のノードからガウス点への補間行列
  * `gradient1d`:                1次元のノードからガウス点への勾配行列

# キーワード引数:

  * `numberelements1d = 1`:      マクロ要素基底のためのサブ要素数

# 戻り値:

  * テンソル積基底オブジェクト
