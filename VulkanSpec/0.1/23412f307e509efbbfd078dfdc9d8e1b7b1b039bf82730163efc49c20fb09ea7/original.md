Specification for a structure parameter.

```julia
struct SpecStructMember <: VulkanSpec.Spec
```

  * `parent::Any`: Name of the parent structure.
  * `name::Symbol`: Identifier.
  * `type::Union{Expr, Symbol}`: Expression of its idiomatic Julia type.
  * `is_constant::Bool`: If constant, cannot be mutated by Vulkan functions.
  * `is_externsync::Bool`: Whether it must be externally synchronized before calling any function which uses the parent structure.
  * `requirement::VulkanSpec.PARAM_REQUIREMENT`: [`PARAM_REQUIREMENT`](@ref) classification.
  * `len::Union{Nothing, Expr, Symbol}`: Name of the member (of the same structure) which represents its length. `Nothing` for non-vector types.
  * `arglen::Vector{Union{Expr, Symbol}}`: Name of the members (of the same structure) it is a length of.
  * `autovalidity::Bool`: Whether automatic validity documentation is enabled. If false, this means that the member may be an exception to at least one Vulkan convention.
