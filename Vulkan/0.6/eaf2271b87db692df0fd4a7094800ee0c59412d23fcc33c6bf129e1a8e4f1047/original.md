Device property that enables a SPIR-V capability when supported.

```julia
struct PropertyCondition
```

  * `type::Symbol`: Name of the property structure relevant to the condition.
  * `member::Symbol`: Member of the property structure to be tested.
  * `core_version::Union{Nothing, VersionNumber}`: Required core version of the Vulkan API, if any.
  * `extension::Union{Nothing, String}`: Required extension, if any.
  * `is_bool::Bool`: Whether the property to test is a boolean. If not, then it will be a bit from a bitmask.
  * `bit::Union{Nothing, Symbol}`: Name of the bit enum that must be included in the property, if the property is not a boolean.
