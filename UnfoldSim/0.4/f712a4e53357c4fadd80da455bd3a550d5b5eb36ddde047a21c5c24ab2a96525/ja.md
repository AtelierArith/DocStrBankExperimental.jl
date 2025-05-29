```
simulate_interonset_distances(rng, onset::AbstractOnset, design::AbstractDesign)
```

それぞれの分布からサンプリングすることによって、インターオンセット距離ベクトルを生成します（サンプル単位）。

# 引数

  * `rng`: プロセスを再現可能にするための乱数生成器（RNG）。
  * `onset::AbstractOnset`: サンプリングするインターオンセット距離分布。
  * `design::AbstractDesign`: 条件と共変量を持つ実験デザイン。

# 戻り値

  * `Vector{Integer}`: サンプル単位のインターオンセット距離。これはオンセット間の距離であり、遅延ではありません。

# 例

```julia-repl
# 実験デザインを作成
julia> design_single = SingleSubjectDesign(;
           conditions = Dict(
               :stimulus_type => ["natural", "artificial"],
               :contrast_level => range(0, 1, length = 3),
           ),
       );

# インターオンセット距離分布を作成
julia> onset_distribution = LogNormalOnset(3, 0.5, 5, nothing);

julia> using StableRNGs

julia> simulate_interonset_distances(StableRNG(1), onset_distribution, design_single)
6-element Vector{Int64}:
 20
 26
 34
 18
 12
 23
```

詳細は [`simulate_onsets`](@ref) を参照してください。
