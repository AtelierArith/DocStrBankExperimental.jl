Specification for handle types.

A handle may possess a parent. In this case, the handle can only be valid if its parent is valid.

Some handles are dispatchable, which means that they are represented as opaque pointers. Non-dispatchable handles are 64-bit integer types, and may encode information directly into their value.

```julia
struct SpecHandle <: VulkanSpec.Spec
```

  * `name::Symbol`: Name of the handle type.
  * `parent::Union{Nothing, Symbol}`: Name of the parent handle, if any.
  * `is_dispatchable::Bool`: Whether the handle is dispatchable or not.
