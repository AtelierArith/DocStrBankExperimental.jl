```julia
TensorH1UniformHProlongationBasis(
    numbernodes1d,
    numbercomponents,
    dimension,
    numberfineelements1d,
)
```

均等に配置された点でのテンソル積 h-延長基底

# 引数:

  * `numbernodes1d::Int`:         要素ごとの均等に配置されたノードの数
  * `numbercomponents::Int`:      コンポーネントの数
  * `dimension::Int`:             基底の次元
  * `numberfineelements1d::Int`:  細かいグリッド要素の数

# 戻り値:

  * 均等に配置されたノードオブジェクト上の H1 ラグランジュテンソル積 h-延長基底

# 例:

```jldoctest
# 均等に配置されたノード上の H1 ラグランジュテンソル積 h-延長基底を生成
basis = TensorH1UniformHProlongationBasis(4, 3, 2, 2);

# 検証
println(basis)

# 出力

tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 7
    numbercomponents: 3
    dimension: 2
```
