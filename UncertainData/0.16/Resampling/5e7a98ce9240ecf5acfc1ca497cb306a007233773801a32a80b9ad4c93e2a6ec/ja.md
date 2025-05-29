```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Vector{SamplingConstraint}, 
	constraint_vals::SamplingConstraint,
	n::Int) -> Vector{Tuple{Vector{Float64}, Vector{Float64}}}
```

不確実なインデックス値データセットの `n` 実現を要素ごとに再サンプリングします。

すべてのインデックス値に対して同じサンプリング制約 `constraint_idxs` を強制し、i 番目のデータ値にはサンプリング制約 `constraint_vals[i]` を使用します。
