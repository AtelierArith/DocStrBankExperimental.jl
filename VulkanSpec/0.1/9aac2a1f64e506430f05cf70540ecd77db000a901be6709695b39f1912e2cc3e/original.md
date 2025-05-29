Specification for a flag type `name` that is a type alias of `typealias`. Can be associated with a bitmask structure, in which case the `bitmask` number is set to the corresponding `SpecBitmask`.

```julia
struct SpecFlag <: VulkanSpec.Spec
```

  * `name::Symbol`: Name of the flag type.
  * `typealias::Symbol`: The type it aliases.
  * `bitmask::Union{Nothing, VulkanSpec.SpecBitmask}`: Bitmask, if applicable.
