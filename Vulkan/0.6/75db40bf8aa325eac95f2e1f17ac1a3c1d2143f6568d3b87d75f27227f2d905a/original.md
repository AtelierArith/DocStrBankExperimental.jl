Extension: VK_KHR_video_queue

Arguments:

  * `memory_bind_index::UInt32`
  * `memory_requirements::_MemoryRequirements`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionMemoryRequirementsKHR.html)

```julia
_VideoSessionMemoryRequirementsKHR(
    memory_bind_index::Integer,
    memory_requirements::Vulkan._MemoryRequirements;
    next
) -> Vulkan._VideoSessionMemoryRequirementsKHR

```
