Specification for an alias of the form `const <name> = <alias>`.

```julia
struct SpecAlias{S<:VulkanSpec.Spec} <: VulkanSpec.Spec
```

  * `name::Symbol`: Name of the new alias.
  * `alias::VulkanSpec.Spec`: Aliased specification element.
