```
rand([rng::AbstractRNG], kdpp::kDeterminantalPointProcess)::Vector{Int}
rand([rng::AbstractRNG], kdpp::kDeterminantalPointProcess, n::Int)::Vector{Vector{Int}}
```

k-DPP [1] からの正確なサンプリング。`kDeterminantalPointProcess` に渡された `L` 行列に関するインデックスのベクトルを返します。各ベクトルのサイズは `k` です。
