```julia
TensorH1UniformHProlongationMacroBasis(
    numbernodes1d,
    numbercomponents,
    dimension,
    numbercoarseelements1d,
    numberfineelements1d,
)
```

均等に配置された点でのテンソル積マクロ要素 h-延長基底

# 引数:

  * `numbernodes1d::Int`:           要素ごとの均等に配置されたノードの数
  * `numbercomponents::Int`:        コンポーネントの数
  * `dimension::Int`:               基底の次元
  * `numbercoarseelements1d::Int`:  マクロ要素内の粗いグリッド要素の数
  * `numberfineelements1d::Int`:    マクロ要素内の細かいグリッド要素の数

# 戻り値:

  * 均等に配置されたノードオブジェクト上の H1 ラグランジュテンソル積 h-延長マクロ要素基底

# 例:

```jldoctest
# 均等に配置されたノード上の H1 ラグランジュテンソル積 h-延長マクロ要素基底を生成
basis = TensorH1UniformHProlongationMacroBasis(4, 1, 2, 2, 4);

# 検証
println(basis)

# 出力

マクロ要素テンソル積基底:
    numbernodes1d: 7
    numberquadraturepoints1d: 13
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
```
