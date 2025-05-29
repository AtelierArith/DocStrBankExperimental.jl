```
struct LowRankLDLT{T,Tr,C<:RankCheck}
    L::Matrix{T}
    singular_values::Vector{Tr}
    rank_check::C
end
```

低ランクコレスキー分解 `L * Diagonal(singular_values) * L'` は、特異値 `singular_values[1] > ... > singular_values[n]` を持つ `n x n` 行列のサイズ `(n, r)` です。ランクは、[`rank_from_singular_values`](@ref) 関数を介して `rank_check` を使用して `singular_values` に基づいて選択されました。
