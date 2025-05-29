Arguments:

  * `memory_requirements::_MemoryRequirements`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryRequirements2.html)

```julia
_MemoryRequirements2(
    memory_requirements::Vulkan._MemoryRequirements;
    next
) -> Vulkan._MemoryRequirements2

```
