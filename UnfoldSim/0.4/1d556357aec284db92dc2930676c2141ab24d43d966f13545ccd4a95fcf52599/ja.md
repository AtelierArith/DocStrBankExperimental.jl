```
simulate_component(rng, c::MixedModelComponent, design::AbstractDesign, return_parameters = false)
```

MixedModelを生成し、与えられたパラメータ `c.β` と `c.σs` に従ってデータをシミュレートします。

# キーワード引数

  * `return_parameters::Bool = false`: 基底関数を重み付けするために使用されたイベントごとのパラメータを返すために使用できます。シミュレーションされた内容を確認するのに役立つことがあります。

# 戻り値

  * `Matrix{Float64}`: イベントデータフレーム内の各イベントに対するシミュレートされたコンポーネント。出力の次元は `length(c.basis) x length(design)` です。

# 注意事項

1. MixedModels/Simは、残差のホワイトノイズなしでデータをシミュレートすることを許可していません。自分のノイズを持ちたいので、MixedModelsノイズを取り除くために以下のトリックを使用します：

実際には、指定された `σs` を10*000倍にスケールアップし、ホワイトノイズレベル `σ = 0.0001` を要求します。MixedModels/Sim内部では、`σs` は `σ` に対して相対的であり、したがって正しく正規化され、ノイズはランダム効果の10*000倍小さく保たれます。

ランダム効果 `σs` が固定効果に比べて非常に大きい場合、このトリックが奇妙な数値的問題を引き起こす可能性があることを除外することはできません。

2. 現在、固定効果とランダム効果に異なる基底を使用することはできません。これが必要な場合、いくつかのコードスカフォールドが利用可能ですが、現時点ではコメントアウトされており、少しの実装作業が必要です。

# 例

```julia-repl
julia> design = MultiSubjectDesign(; n_subjects = 2, n_items = 6, items_between = Dict(:cond => ["A", "B"]));

julia> c = UnfoldSim.MixedModelComponent([0, 1, 1, 0], @formula(0 ~ 1 + cond + (1|subject)), [1, 2], Dict(:subject => [2],), Dict());

julia> using StableRNGs

julia> simulate_component(StableRNG(1), c, design)
4×12 Matrix{Float64}:
 -0.0      -0.0       -0.0      -0.0       -0.0     -0.0       0.0       0.0      0.0       0.0      0.0       0.0
 -2.70645  -0.706388  -2.70632  -0.706482  -2.7066  -0.706424  0.325722  2.32569  0.325627  2.32564  0.325468  2.32565
 -2.70645  -0.706388  -2.70632  -0.706482  -2.7066  -0.706424  0.325722  2.32569  0.325627  2.32564  0.325468  2.32565
 -0.0      -0.0       -0.0      -0.0       -0.0     -0.0       0.0       0.0      0.0       0.0      0.0       0.0

julia> simulate_component(StableRNG(1), c, design, return_parameters = true)
1×12 Matrix{Float64}:
 -2.70645  -0.706388  -2.70632  -0.706482  -2.7066  -0.706424  0.325722  2.32569  0.325627  2.32564  0.325468  2.32565
```
