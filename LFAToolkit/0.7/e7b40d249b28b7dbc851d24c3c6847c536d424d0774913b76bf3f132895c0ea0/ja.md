```julia
TensorHProlongationBasis(
    coarsenodes1d,
    finenodes1d,
    numbercomponents,
    dimension,
    numberfineelements1d,
)
```

テンソル積 h-延長基底

# 引数:

  * `coarsenodes1d::AbstractArray{Float64,1}`:  1次元の粗いグリッドノード座標
  * `finenodes1d::AbstractArray{Float64,1}`:    1次元の細かいグリッドノード座標
  * `numbercomponents::Int`:                    コンポーネントの数
  * `dimension::Int`:                           基底の次元
  * `numberfineelements1d::Int`:                細かいグリッド要素の数

# 戻り値:

  * H1 ラグランジュテンソル積 h-延長基底オブジェクト
