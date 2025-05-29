```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Vector{SamplingConstraint}, 
	constraint_vals::SamplingConstraint) -> Tuple{Vector{Float64}, Vector{Float64}}
```

不確実なインデックス値データセットを要素ごとに再サンプリングします。

i 番目のインデックス値に一意のサンプリング制約 `constraint_idxs[i]` を強制します。また、i 番目のデータ値に一意のサンプリング制約 `constraint_vals[i]` を強制します。
