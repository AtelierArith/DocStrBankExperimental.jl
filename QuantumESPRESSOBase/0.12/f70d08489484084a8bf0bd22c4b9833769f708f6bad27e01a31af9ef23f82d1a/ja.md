```
optionpool(card::Card)
optionpool(T::Type{<:Card})
```

`Card` または `Card` 型の許可されたオプションを返します。

# 例

```jldoctest
julia> optionpool(AtomicPositionsCard)
("alat", "bohr", "angstrom", "crystal", "crystal_sg")

julia> optionpool(CellParametersCard)
("alat", "bohr", "angstrom")

julia> optionpool(SpecialPointsCard)
("tpiba", "crystal", "tpiba_b", "crystal_b", "tpiba_c", "crystal_c")
```
