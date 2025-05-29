```
print_subtypes(T::Type; kwargs...)
print_subtypes(io::IO, T::Type; kwargs...)
print_subtypes(f, io::IO, T::Type; kwargs...)
```

は `AbstractTrees.print_tree` によって `T` のサブタイプを出力します。

## 例

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
