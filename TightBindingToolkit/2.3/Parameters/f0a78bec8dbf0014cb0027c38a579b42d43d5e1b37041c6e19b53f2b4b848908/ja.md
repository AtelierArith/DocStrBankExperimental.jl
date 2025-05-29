```julia
AddSimilarBond!(param::Param{T, R}, uc::UnitCell{T2}, bond::Bond{T} ;  subs::Vector{Int64}=collect(1:length(uc.basis)), checkOffsetRange::Int64=2) where {T, R}
AddSimilarBond!(param::Param{T, R}, uc::UnitCell{T2}, base::Int64, target::Int64, offset::Vector{Int64}, mat::Array{ComplexF64, T}, dist::Float64, label::String ;  subs::Vector{Int64}=collect(1:length(uc.basis)), checkOffsetRange::Int64=2) where {T, R}
```

完全に等方的ではないが、依然として翻訳によって関連する結合を追加するための関数（単位セルの原始的なものではなく、基礎的な格子の原始的なものによって）。
