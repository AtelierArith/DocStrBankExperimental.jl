```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Vector{SamplingConstraint}, 
	constraint_vals::SamplingConstraint) -> Tuple{Vector{Float64}, Vector{Float64}}
```

不確実なインデックス値データセットを要素ごとに再サンプリングします。

ユニークなサンプリング制約 `constraint_idxs[i]` を i 番目のインデックス値と i 番目のデータ値の両方に強制します。
