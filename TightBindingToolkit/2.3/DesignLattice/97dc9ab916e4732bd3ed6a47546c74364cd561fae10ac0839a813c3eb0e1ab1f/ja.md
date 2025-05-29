```julia
RemoveLatticeBonds!(lattice::Lattice{T} , label::String ; null_dist::Float64 = -1.0, null_label::String = "-") where {T}
```

指定された `label` を持つ格子結合を削除します。
