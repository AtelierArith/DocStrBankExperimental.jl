```
scaled_LHC_sampling_plan(search_range::Array{Tuple{Float64,Float64},1},num_samples,sampling_plan_opt_gens;trace::Symbol=:silent)
```

`search_range` にスケーリングされたラテンハイパーキューブサンプリングプランを作成します。ここで `size(plan) = (num_dimensions,num_samples)` です。
