```
rand([rng::AbstractRNG], dpp::DeterminantalPointProcess)::Vector{Int}
rand([rng::AbstractRNG], dpp::DeterminantalPointProcess, n::Int)::Vector{Vector{Int}}
```

DPP [1] からの正確なサンプリング。`DeterminantalPointProcess` に渡された `L` 行列に関するインデックスのベクトルを返します。各ベクトルの長さは 0 から `size(L,1)` まで変動する可能性があります。
