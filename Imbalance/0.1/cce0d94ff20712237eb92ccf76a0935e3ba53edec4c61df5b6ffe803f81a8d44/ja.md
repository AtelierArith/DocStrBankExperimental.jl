```
generate_imbalanced_data(
    num_rows, num_continuous_feats;
    means=nothing, min_sep=1.0, stds=nothing,
    num_vals_per_category = [],
    class_probs = [0.8, 0.2],
    type= "ColTable", insert_y= nothing,
    rng= default_rng(),
)
```

`num_rows` の観測値を生成し、各クラスの与えられた確率を尊重してターゲット `y` を生成します。特定の平均と分散を持つ連続特徴と、各変数のレベル数に基づいてカテゴリ特徴を生成することをサポートします。

# 引数

  * `num_rows::Integer`: 生成する観測値の数
  * `num_continuous_feats::Integer`: 生成する連続特徴の数
  * `means::AbstractVector=nothing`: 各連続特徴の平均のベクトル（`num_continuous_feats` と同じ長さでなければなりません）。`nothing` の場合はランダムに設定されます
  * `min_sep::AbstractFloat=1.0`: ランダムに選ばれた2つの平均の間の最小距離。平均が与えられている場合は影響しません。
  * `stds::AbstractVector=nothing`: 各連続特徴の標準偏差のベクトル（`num_continuous_feats` と同じ長さでなければなりません）。`nothing` の場合はランダムに設定されます
  * `num_vals_per_category::AbstractVector=[]`: 各追加カテゴリ特徴のレベル数のベクトル。このベクトルからカテゴリ特徴の数が推測されます。
  * `class_probs::AbstractVector{<:AbstractFloat}=[0.8, 0.2]`: 各クラスの確率のベクトル。このベクトルからクラスの数が推測されます。
  * `type::AbstractString="ColTable"`: `"Matrix"` または `"ColTable"` のいずれか。後者の場合、ベクトルの名前付きタプルが返されます。
  * `insert_y::Integer=nothing`: `nothing` でない場合、テーブルの指定されたインデックスにクラスラベル列を挿入します
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: 擬似乱数生成器。整数の場合、Julia `VERSION` がサポートしている場合は `Random.Xoshiro(seed)` の `seed` として使用されます。それ以外の場合は `Random.MersenneTwister(seed)` を使用します。

# 戻り値

  * `X:`: 生成された不均衡データを持つ列テーブルまたは行列で、`num_rows` 行と `num_continuous_feats + length(num_vals_per_category)` 列を持ちます。`insert_y` が整数として指定されている場合、`y` も指定されたインデックスに追加の列として挿入されます。
  * `y::CategoricalArray`: ラベル $0$, $1$, $2$, ..., $k-1$ を持つクラスラベルの抽象ベクトルで、ここで `k=length(class_probs)`

# 例

```julia
using Imbalance
using Plots

num_rows = 500
num_features = 2
# 平均と標準偏差を考慮して連続特徴を生成
X, y = generate_imbalanced_data(
	num_rows,
	num_features;
	means = [1.0, 4.0, [7.0 9.0]],
	stds = [1.0, [0.5 0.8], 2.0],
	class_probs=[0.5, 0.2, 0.3],
	type="Matrix",
	rng = 42,
)

p = plot()
[scatter!(p, X[:, 1][y.==yi], X[:, 2][y.==yi], label = "$y=yi$") for yi in unique(y)]

julia> plot(p)
```

![generated data](../../assets/gen_one.png)

```julia
# ランダムな平均と標準偏差を持つ連続特徴を生成
X, y = generate_imbalanced_data(
	num_rows,
	num_features;
    min_sep=0.3,      
	class_probs=[0.5, 0.2, 0.3],
	type="Matrix",
	rng = 33,
)

p = plot()
[scatter!(p, X[:, 1][y.==yi], X[:, 2][y.==yi], label = "$y=yi$") for yi in unique(y)]

julia> plot(p)
```

![generated data](../../assets/gen_two.png)

```julia
num_rows = 500
num_features = 2
X, y = generate_imbalanced_data(
	num_rows,
	num_features;
    num_vals_per_category = [3, 5, 2],
	class_probs=[0.9, 0.1],
	insert_y=4,
	type="ColTable",
	rng = 33,
)

julia> X
(Column1 = [0.883, 0.9, 0.577  …  0.887,],
 Column2 = [0.578, 0.718, 0.378  …  0.573,],
 Column3 = [2.0, 2.0, 3.0, …  2.0,],
 Column4 = [0.0, 0.0, 0.0, …  0.0,],
 Column5 = [2.0, 3.0, 4.0, …  4.0,],
 Column6 = [1.0, 1.0, 2.0, …  1.0,],)
```
