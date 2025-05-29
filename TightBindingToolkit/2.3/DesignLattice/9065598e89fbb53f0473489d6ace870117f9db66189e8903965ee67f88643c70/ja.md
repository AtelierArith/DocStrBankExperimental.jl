```julia
ModifyLattice!(lattice::Lattice{T}, param::Param{T}) where {T}
ModifyLattice!(lattice::Lattice{T}, params::Vector{Param{T}}) where {T}
```

`params` に与えられた `Param` オブジェクトが変更されると、格子が修正されます。
