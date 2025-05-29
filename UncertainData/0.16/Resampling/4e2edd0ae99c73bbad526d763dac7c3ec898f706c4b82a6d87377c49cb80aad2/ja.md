```
resample(udata::UncertainIndexValueDataset, 
	constraint::Union{SamplingConstraint, Vector{SamplingConstraint}}) -> Tuple{Vector{Float64}, Vector{Float64}}
```

不確実なインデックス値データセットを要素ごとに再サンプリングします。

提供されたサンプリング `constraint` をデータセット内のすべての不確実な値に対して強制します。これは、インデックスとデータ値の両方に適用されます。

単一の制約が提供された場合、その制約はすべての値に適用されます。制約のベクトル（値の数と同じ数）が提供された場合、制約はインデックスとデータ値の両方に要素ごとに適用されます。
