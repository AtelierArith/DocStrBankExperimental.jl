```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Vector{SamplingConstraint}, 
	constraint_vals::SamplingConstraint,
	n::Int) -> Vector{Tuple{Vector{Float64}, Vector{Float64}}}
```

不確実なインデックス値データセットの `n` 回の実現を要素ごとに再サンプリングします。

一意のサンプリング制約 `constraint_idxs[i]` を i 番目のインデックス値と i 番目のデータ値の両方に強制します。
