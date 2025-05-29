```julia
shannon_entropy(p::AbstractArray{R<:Real, 1}) -> Any

```

確率分布のシャノンエントロピーを計算します: `H(p) = -∑ pᵢlog(pᵢ)`。
