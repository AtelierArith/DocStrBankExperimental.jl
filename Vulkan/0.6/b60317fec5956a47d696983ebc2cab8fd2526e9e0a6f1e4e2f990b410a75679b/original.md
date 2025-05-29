Extension: VK_EXT_memory_priority

Arguments:

  * `priority::Float32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryPriorityAllocateInfoEXT.html)

```julia
MemoryPriorityAllocateInfoEXT(
    priority::Real;
    next
) -> Vulkan.MemoryPriorityAllocateInfoEXT

```
