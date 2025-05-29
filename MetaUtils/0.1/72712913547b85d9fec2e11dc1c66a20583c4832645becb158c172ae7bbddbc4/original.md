```
print_subtypes(T::Type; kwargs...)
print_subtypes(io::IO, T::Type; kwargs...)
print_subtypes(f, io::IO, T::Type; kwargs...)
```

prints the subtypes of `T` by `AbstractTrees.print_tree`.

## Example

```julia
julia> print_subtypes(AbstractRange)
AbstractRange
├─ LinRange
├─ OrdinalRange
│  ├─ AbstractUnitRange
│  │  ├─ Base.IdentityUnitRange
│  │  ├─ Base.OneTo
│  │  ├─ Base.Slice
│  │  └─ UnitRange
│  └─ StepRange
└─ StepRangeLen
```
