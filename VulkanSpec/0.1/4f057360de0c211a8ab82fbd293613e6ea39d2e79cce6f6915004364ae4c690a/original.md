Specification for a function parameter.

```julia
struct SpecFuncParam <: VulkanSpec.Spec
```

  * `parent::Any`: Name of the parent function.
  * `name::Symbol`: Identifier.
  * `type::Union{Expr, Symbol}`: Expression of its idiomatic Julia type.
  * `is_constant::Bool`: If constant, cannot be mutated by Vulkan functions.
  * `is_externsync::Bool`: Whether it must be externally synchronized before calling the function.
  * `requirement::VulkanSpec.PARAM_REQUIREMENT`: [`PARAM_REQUIREMENT`](@ref) classification.
  * `len::Union{Nothing, Expr, Symbol}`: Name of the parameter (of the same function) which represents its length. `Nothing` for non-vector types. Can be an expression of a parameter.
  * `arglen::Vector{Symbol}`: Name of the parameters (of the same function) it is a length of.
  * `autovalidity::Bool`: Whether automatic validity documentation is enabled. If false, this means that the parameter may be an exception to at least one Vulkan convention.
