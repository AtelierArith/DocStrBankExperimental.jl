```
Atom(identifier::AtomId, position::AbstractVector; kwargs...)
Atom(identifier::AtomId, position::AbstractVector, velocity::AbstractVector; kwargs...)
Atom(; atomic_number, position, velocity=zeros(D)u"bohr/s", kwargs...)
```

与えられた直交座標 `position` に位置する原子を構築し、（オプションで）指定された直交 `velocity` を持たせます。`AtomId = Union{Symbol,AbstractString,Integer,ChemicalSymbol}` であることに注意してください。

サポートされている `kwargs` には `species`、`mass`、およびユーザー固有のカスタムプロパティが含まれます。
