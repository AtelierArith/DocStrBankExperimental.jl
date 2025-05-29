```
guesswork_lower_bound(
    p::AbstractVector{T},
    ρBs::AbstractVector{<:AbstractMatrix};
    solver,
    c = T[1:length(p)..., 10_000],
    verbose::Bool = false,
)
```

[`guesswork`](@ref) の引数の意味については、こちらを参照してください。プライマル SDP の緩和版を解くことによって、最適な期待推測回数の下限を計算します。`J` 状態の場合、2 つの線形制約に従う `J^2` の PSD 変数のみが必要です。
