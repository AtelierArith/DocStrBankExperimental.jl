Specification for a structure.

```julia
struct SpecStruct <: VulkanSpec.Spec
```

  * `name::Symbol`: Name of the structure.
  * `type::VulkanSpec.StructType`: [`StructType`](@ref) classification.
  * `is_returnedonly::Bool`: Whether the structure is only meant to be filled in by Vulkan functions, as opposed to being constructed by the user.

    Note that the API may still request the user to provide an initialized structure, notably as part of `pNext` chains for queries.

  * `extends::Vector{Symbol}`: Name of the structures it extends, usually done through the original structures' `pNext` argument.
  * `members::StructArrays.StructVector{VulkanSpec.SpecStructMember}`: Structure members.
