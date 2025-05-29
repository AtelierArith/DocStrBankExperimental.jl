```
resample(udata::UncertainIndexValueDataset, 
	constraint::SamplingConstraint) -> Tuple{Vector{Float64}, Vector{Float64}}
```

不確実なインデックス値データセットを要素ごとに再サンプリングします。

提供されたサンプリング `constraint` をデータセット内のすべての不確実な値、すなわちインデックスとデータ値の両方に適用します。
