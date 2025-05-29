Specification for an enumeration type.

```julia
struct SpecEnum <: VulkanSpec.Spec
```

  * `name::Symbol`: Name of the enumeration type.
  * `enums::StructArrays.StructVector{VulkanSpec.SpecConstant}`: Vector of possible enumeration values.
