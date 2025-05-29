```
compact_groups!(
    group_indices::AbstractVector{<:Integer},
)::Int
```

与えられた配列 `group_indices` は、ある軸の各エントリを非負のグループインデックスに割り当てます（ゼロは「グループなし」を意味します）。これをインプレースで圧縮し、グループインデックスを `1...N` にし、`N` を返します。
