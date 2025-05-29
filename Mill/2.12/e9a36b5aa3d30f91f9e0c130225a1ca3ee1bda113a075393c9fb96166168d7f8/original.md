```
AlignedBags{T <: Integer} <: AbstractBags{T}
```

[`AlignedBags`](@ref) struct stores indices of bags' instances in one or more `UnitRange{T}`s. This is only possible if instances of every bag are stored in one contiguous block.

See also: [`ScatteredBags`](@ref).
