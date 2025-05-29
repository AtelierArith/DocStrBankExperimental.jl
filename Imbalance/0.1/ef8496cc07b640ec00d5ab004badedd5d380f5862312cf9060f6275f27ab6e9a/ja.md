```
checkbalance(y; reference="majority")
```

`StatsBase.countmap`の視覚的バージョンで、何も返さず、データセット内の各クラスに属する観測値の数と、それらのクラスのサイズに対する割合を印刷します。

# 引数

  * `y::AbstractVector`: 不均衡をテストするためのカテゴリカル値のベクトル
  * `reference="majority"`: `"majority"`または`"minority"`のいずれかで、割合が多数派または少数派クラスのサイズに対して相対的であるべきかを決定します。

# 例

```julia
num_rows = 50000
num_features = 2
X, y = generate_imbalanced_data(
	num_rows,
	num_features;
	class_probs=[0.8, 0.2],
	type="Matrix",
	rng = 42,
)

julia> Imbalance.checkbalance(y; ref="majority")
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇ 10034 (25.1%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 39966 (100.0%) 

julia> Imbalance.checkbalance(y; ref="minority")
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇ 10034 (100.0%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 39966 (398.3%) 
```
