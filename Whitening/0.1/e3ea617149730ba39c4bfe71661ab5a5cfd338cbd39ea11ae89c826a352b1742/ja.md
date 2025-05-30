```
GeneralizedPCA(μ::AbstractVector{T}, Σ::AbstractMatrix{T};
               num_components::Union{Int, Nothing}=nothing,
               vmin::Union{T, Nothing}=nothing,
               rtol::Union{T, Nothing}=nothing) where {T<:Base.IEEEFloat}
```

平均ベクトル `μ` ∈ ℝⁿ と共分散行列 `Σ` ∈ ℝⁿˣⁿ から一般化PCAトランスフォーマーを構築します。`Σ` は対称で半正定値でなければなりません。

トランスフォーマーの出力次元 `m` はオプション引数から決定されます。ここで、

1. 0 ≤ `num_components` ≤ n は事前に決定されたサイズです。
2. 0 ≤ `vmin` ≤ 1 は総平方交差共分散の割合であり、したがって `m` は `sum(λ[1:m]) ≥ vmin*sum(λ)` を満たす最小の値です。ここで $λᵢ, i=1,…,n$ は `Σ` の固有値で、降順に並んでいます。
3. `rtol` は `rtol*λ₁` より大きい固有値の数に対する相対許容誤差であり、ここで `λ₁` は `Σ` の最大固有値です。

3つのオプションのいずれも提供されない場合、デフォルトは `rtol = n*eps(T)` です。2つ以上のオプションが提供された場合、結果のサイズの最小値が選択されます。
