```julia
ExpandBonds!(ucOG::UnitCell{T}, ucNew::UnitCell{T} ; OffsetRange::Int64 = 2)
```

An in-place version of `ExpandUnitCell` which works with the new primitive vectors given in `ucNew`.
