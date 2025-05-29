API ユニオン型。

```julia
struct Unions <: VulkanSpec.Collection{VulkanSpec.SpecUnion}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecUnion, @NamedTuple{name::Vector{Symbol}, types::Vector{Vector{Union{Expr, Symbol}}}, fields::Vector{Vector{Symbol}}, selectors::Vector{Vector{Symbol}}, is_returnedonly::Vector{Bool}}, Int64}`
