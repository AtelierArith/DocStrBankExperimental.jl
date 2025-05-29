```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::SamplingConstraint, 
	constraint_vals::SamplingConstraint) -> Tuple{Vector{Float64}, Vector{Float64}}
```

不確実なインデックス値データセットを要素ごとに再サンプリングします。

すべてのインデックス値に同じサンプリング制約 `constraint_idxs` を適用し、すべてのデータ値に `constraint_vals` サンプリング制約を適用します。
