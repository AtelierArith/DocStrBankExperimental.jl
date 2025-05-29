```
resample(uv::AbstractUncertainIndexDataset, constraint::Vector{<:SamplingConstraint})
```

不確実なインデックスデータセットの実現を引き出します。それは、データセットに含まれる不確実な値に従い、提供されたサンプリング制約に従ってデータセット内の値を供給する分布を制約します。
