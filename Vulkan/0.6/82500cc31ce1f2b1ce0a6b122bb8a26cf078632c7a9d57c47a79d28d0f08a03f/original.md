Arguments:

  * `prefers_dedicated_allocation::Bool`
  * `requires_dedicated_allocation::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryDedicatedRequirements.html)

```julia
_MemoryDedicatedRequirements(
    prefers_dedicated_allocation::Bool,
    requires_dedicated_allocation::Bool;
    next
) -> Vulkan._MemoryDedicatedRequirements

```
