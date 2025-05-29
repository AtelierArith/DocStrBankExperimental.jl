```
struct LowRankLDLT{T,Tr,C<:RankCheck}
    L::Matrix{T}
    singular_values::Vector{Tr}
    rank_check::C
end
```

Low-Rank cholesky decomposition `L * Diagonal(singular_values) * L'` of size `(n, r)` of a `n x n` matrix with singular values `singular_values[1] > ... > singular_values[n]`. The rank was chosen given `singular_values` using `rank_check` via the [`rank_from_singular_values`](@ref) function.
