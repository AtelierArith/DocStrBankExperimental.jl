```
model_infill(search_range::Vector{Tuple{Float64,Float64}},plan::AbstractArray{T,2},
samples::AbstractArray{T,2},sm_interpolant; options::Options=Options()) where T
```

提供されたオプションに基づいて新しいサンプルの位置を計算するインフィル関数。返されるオプションは、インフィル目的関数を循環するのを容易にするために更新されます。

...

# 引数

  * `search_range::Vector{Tuple{Float64,Float64}`:   各次元の下限と上限を含むタプルのベクトル。 `length(search_range)` は次元の数に等しい。
  * `plan::AbstractArray{T,2}`:    各列が1つの点の位置に対応するサンプルの位置。   `size(plan) = (num_dimensions,num_samples)`。
  * `samples::AbstractArray{T,2}`:   各サンプル位置での関数値。各列には対応するプラン位置からの1つの値が含まれます。 `size(samples) = (1,num_samples)`。
  * `options=Options()`:    サロゲートインフィルをカスタマイズするために利用可能なすべてのオプション。

...
