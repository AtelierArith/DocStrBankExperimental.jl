```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Union{SamplingConstraint, Vector{SamplingConstraint}}, 
	constraint_vals::Union{SamplingConstraint, Vector{SamplingConstraint}}) -> Tuple{Vector{Float64}, Vector{Float64}}
```

不確実なインデックス値データセットを要素ごとに再サンプリングします。

インデックスとデータ値に対して別々のサンプリング制約を強制します。

単一の制約が提供された場合、その制約はすべての値に適用されます。制約のベクトル（値の数だけある場合）が提供された場合、制約は要素ごとに適用されます。
