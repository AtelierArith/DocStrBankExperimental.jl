```julia
TensorMacroElementBasisFrom1D(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension,
    numberelements1d,
    basis1dmicro;
    overlapquadraturepoints = false,
)
```

1次元単一要素テンソル積基底からのテンソル積マクロ要素基底

# 引数:

  * `numbernodes1d::Int`:             1次元の基底ノードの数
  * `numberquadraturepoints1d::Int`:  1次元の数値積分点の数
  * `numbercomponents::Int`:          コンポーネントの数
  * `dimension::Int`:                 基底の次元
  * `numberelements1d::Int`:          マクロ要素内の要素の数
  * `basis1dmicro::TensorBasis`:      複製する1次元マイクロ要素基底

# キーワード引数:

  * `overlapquadraturepoints::Bool = false`:  要素間での数値積分点の重複、延長のため

# 戻り値:

  * テンソル積マクロ要素基底オブジェクト
