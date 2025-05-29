```julia
FillLattice!( lattice::Lattice{T} ; null_dist::Float64 = -1.0, null_label::String = "-") where {T}
```

ラティス内のサイト情報とボンド情報の両方を埋めるためのラッパー関数。
