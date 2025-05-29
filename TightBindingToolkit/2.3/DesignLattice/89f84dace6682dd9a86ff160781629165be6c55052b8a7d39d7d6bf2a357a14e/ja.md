```julia
CreateLattice(uc::UnitCell{T}, param::Param{T}, size::Vector{Int64} , index::Int64=length(param.value) ; null_dist::Float64 = -1.0, null_label::String = "-") --> Lattice{T} where {T}
CreateLattice(uc::UnitCell{T}, params::Vector{Param{T}}, size::Vector{Int64} , indices::Vector{Int64}=length.(getproperty.(params, :value)) ; null_dist::Float64 = -1.0, null_label::String = "-") :: Lattice{T} where {T}
```

`params`で与えられた`Param`オブジェクトを使用して格子を作成します。
