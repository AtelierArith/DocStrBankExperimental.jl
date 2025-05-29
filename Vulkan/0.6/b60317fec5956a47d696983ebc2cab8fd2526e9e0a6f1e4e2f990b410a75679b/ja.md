拡張: VK*EXT*memory_priority

引数:

  * `priority::Float32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryPriorityAllocateInfoEXT.html)

```julia
MemoryPriorityAllocateInfoEXT(
    priority::Real;
    next
) -> Vulkan.MemoryPriorityAllocateInfoEXT

```
