```julia
TensorH1UniformMacroBasis(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension,
    numberelements1d,
)
```

ガウス・ルジャンドル積分法による均等点でのテンソル積マクロ要素基底

# 引数:

  * `numbernodes1d::Int`:             1次元の均等に間隔を空けたノードの数
  * `numberquadraturepoints1d::Int`:  1次元のガウス・ルジャンドル積分点の数
  * `numbercomponents::Int`:          コンポーネントの数
  * `dimension::Int`:                 基底の次元
  * `numberelements1d::Int`:          マクロ要素内の要素の数

# 戻り値:

  * 均等に間隔を空けたノードオブジェクト上のH1ラグランジュテンソル積マクロ要素基底

# 例:

```jldoctest
# 均等に間隔を空けたノード上のH1ラグランジュテンソル積マクロ要素基底を生成
basis = TensorH1UniformMacroBasis(4, 3, 1, 2, 2);

# 検証
println(basis)

# 出力

マクロ要素テンソル積基底:
    numbernodes1d: 7
    numberquadraturepoints1d: 6
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
```
