```julia
UnitCell(lengths::Vector{Float64}) -> Chemfiles.UnitCell
UnitCell(
    lengths::Vector{Float64},
    angles::Vector{Float64}
) -> Chemfiles.UnitCell

```

与えられた `lengths` と `angles` から `UnitCell` を作成します。
