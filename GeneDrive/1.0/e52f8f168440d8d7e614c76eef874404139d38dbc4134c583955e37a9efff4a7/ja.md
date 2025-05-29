```
mutable struct ReleaseStrategy
    release_this_gene_index::Union{Nothing, Int64}=nothing
    release_this_life_stage=nothing
    release_location_force::Union{Nothing, Bool}=nothing
    release_start_time::Union{Nothing,Int64}=nothing
    release_end_time::Union{Nothing,Int64}=nothing
    release_time_interval::Int64=1
    release_size_min_per_timestep::Union{Int64, Float64}=0.0
    release_size_max_per_timestep::Union{Int64,Float64}=9e9
    release_max_over_timehorizon::Union{Int64,Float64}=9e9

end
```

各ノードの運用制約を定義するデータ。

# 引数

  * `release_this_gene_index`: 放出される遺伝子のインデックス。一般的には `get_homozygous_modified` によって定義される。
  * `release_this_life_stage`: 放出されるライフステージ。遺伝子技術に応じて異なる。
  * `release_location_force`: 放出が義務付けられる場所を指定する。MINLPとして意思決定モデルが実行される場合にのみ適用される。
  * `release_start_time`: 放出が開始されることが許可されるタイムステップ（日）。
  * `release_end_time`: 放出が終了することが求められるタイムステップ（日）。
  * `release_time_interval`: 放出が許可される最小タイムステップ間隔（日）。
  * `release_size_min_per_timestep`: 1日に放出される可能性のある生物の最小数。
  * `release_size_max_per_timestep`: 1日に放出される可能性のある生物の最大数。
  * `release_max_over_timehorizon`: 問題のホライズン全体で放出される可能性のある生物の最大数。
