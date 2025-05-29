拡張: VK*KHR*video_queue

引数:

  * `memory_bind_index::UInt32`
  * `memory_requirements::_MemoryRequirements`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionMemoryRequirementsKHR.html)

```julia
_VideoSessionMemoryRequirementsKHR(
    memory_bind_index::Integer,
    memory_requirements::Vulkan._MemoryRequirements;
    next
) -> Vulkan._VideoSessionMemoryRequirementsKHR

```
