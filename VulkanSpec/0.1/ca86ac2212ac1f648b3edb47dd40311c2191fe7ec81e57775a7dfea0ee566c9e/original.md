Specification for a bitmask type that must be formed through a combination of `bits`.

Is usually an alias for a `UInt32` type which carries meaning through its bits.

```julia
struct SpecBitmask <: VulkanSpec.Spec
```

  * `name::Symbol`: Name of the bitmask type.
  * `bits::StructArrays.StructVector{VulkanSpec.SpecBit}`: Valid bits that can be combined to form the final bitmask value.
  * `combinations::StructArrays.StructVector{VulkanSpec.SpecBitCombination}`
  * `width::Integer`
