API handle types.

```julia
struct Handles <: VulkanSpec.Collection{VulkanSpec.SpecHandle}
```

  * `data::StructArrays.StructVector{VulkanSpec.SpecHandle, @NamedTuple{name::Vector{Symbol}, parent::Vector{Union{Nothing, Symbol}}, is_dispatchable::Vector{Bool}}, Int64}`
