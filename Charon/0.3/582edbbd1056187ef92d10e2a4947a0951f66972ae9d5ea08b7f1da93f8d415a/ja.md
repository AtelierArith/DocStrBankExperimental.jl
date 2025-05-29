```
unpackposterior(nsteps::Integer, chains::AbstractVector{<:Tuple{AbstractVector{<:Integer}, AbstractMatrix{<:Real}, AbstractMatrix{<:Real}, AbstractMatrix{<:Real}, AbstractMatrix{Bool}, AbstractMatrix{<:Real}}})
```

MCMCsamplerの出力から無条件の事後分布を計算します。`chains`はサンプラーの出力で、`nsteps`はMCMCサンプルの数です。
