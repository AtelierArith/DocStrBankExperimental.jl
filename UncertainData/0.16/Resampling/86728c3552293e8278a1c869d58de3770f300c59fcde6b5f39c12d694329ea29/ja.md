```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Vector{SamplingConstraint}, 
	constraint_vals::SamplingConstraint,
	n::Int) -> Vector{Tuple{Vector{Float64}, Vector{Float64}}}
```

不確実なインデックス値データセットの `n` 実現を要素ごとに再サンプリングします。

i 番目のインデックス値に対して一意のサンプリング制約 `constraint_idxs[i]` を強制します。また、i 番目のデータ値に対して一意のサンプリング制約 `constraint_vals[i]` を強制します。
