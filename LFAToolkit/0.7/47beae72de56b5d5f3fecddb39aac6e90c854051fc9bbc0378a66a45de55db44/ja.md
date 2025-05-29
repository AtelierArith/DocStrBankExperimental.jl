```julia
NonTensorBasis(
    numbernodes,
    numberquadraturepoints,
    numbercomponents,
    dimension,
    nodes,
    quadraturepoints,
    quadratureweights,
    interpolation,
    gradient;
    numberelements = 1,
)
```

非テンソル基底

# 引数:

  * `numbernodes`:             ノードの数
  * `numberquadraturepoints`:  ガウス点の数
  * `numbercomponents`:        コンポーネントの数
  * `dimension`:               基底の次元
  * `nodes`:                   ノードの座標
  * `quadraturepoints`:        ガウス点の座標
  * `quadratureweights`:       ガウス重み
  * `interpolation`:           ノードからガウス点への補間行列
  * `gradient`:                ノードからガウス点への勾配行列

# キーワード引数:

  * `numberelements = 1`:      サブエレメントの数（マクロエレメント基底用）

# 戻り値:

  * 非テンソル積基底オブジェクト
