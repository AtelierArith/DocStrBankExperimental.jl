```
collect_group_members(
    group_indices::AbstractVector{T},
)::Vector{Vector{T}} where {T <: Integer}
```

非負のグループインデックス（ゼロは「グループなし」を意味する）を各軸のエントリに割り当てる配列 `group_indices` が与えられたとき、グループインデックスがコンパクトである（範囲 `1...N` にある）場合、グループごとに（ソートされた）エントリのインデックスを含むベクトルのベクトルを返します。
