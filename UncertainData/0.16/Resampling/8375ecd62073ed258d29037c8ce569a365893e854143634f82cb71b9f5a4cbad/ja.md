```
resample(udata::UncertainIndexValueDataset, 
	n::Int) -> Vector{Tuple{Vector{Float64}, Vector{Float64}}}
```

不確実なインデックス値データセットから `n` の実現を要素ごとに再サンプリングします。

提供されたサンプリング `constraint` をデータセット内のすべての不確実な値、インデックスとデータ値の両方に強制します。
