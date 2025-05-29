Arguments:

  * `prefers_dedicated_allocation::Bool`
  * `requires_dedicated_allocation::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryDedicatedRequirements.html)

```julia
MemoryDedicatedRequirements(
    prefers_dedicated_allocation::Bool,
    requires_dedicated_allocation::Bool;
    next
) -> Vulkan.MemoryDedicatedRequirements

```
