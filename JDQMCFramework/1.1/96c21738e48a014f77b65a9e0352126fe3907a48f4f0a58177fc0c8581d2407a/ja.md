```
build_hopping_matrix!(
    K::AbstractMatrix{T},
    neighbor_table::Matrix{Int},
    t::AbstractVector{T}
) where {T<:Continuous}
```

隣接テーブル `neighbor_table` と対応するホッピング振幅 `t` を使用してホッピング行列 `K` を構築します。`neighbor_table` の各列は格子内の隣接する軌道のペアを格納しており、`size(neighbor_table,1) = 2` です。
