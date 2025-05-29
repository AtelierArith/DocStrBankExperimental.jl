Specification for a union type.

```julia
struct SpecUnion <: VulkanSpec.Spec
```

  * `name::Symbol`: Name of the union type.
  * `types::Vector{Union{Expr, Symbol}}`: Possible types for the union.
  * `fields::Vector{Symbol}`: Fields which cast the struct into the union types
  * `selectors::Vector{Symbol}`: Selector values, if any, to determine the type of the union in a given context (function call for example).
  * `is_returnedonly::Bool`: Whether the structure is only meant to be filled in by Vulkan functions, as opposed to being constructed by the user.

    Note that the API may still request the user to provide an initialized structure, notably as part of `pNext` chains for queries.
