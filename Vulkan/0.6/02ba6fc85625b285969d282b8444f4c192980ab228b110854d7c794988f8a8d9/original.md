Extension: VK_KHR_video_queue

Arguments:

  * `memory_bind_index::UInt32`
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`
  * `memory_size::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindVideoSessionMemoryInfoKHR.html)

```julia
_BindVideoSessionMemoryInfoKHR(
    memory_bind_index::Integer,
    memory,
    memory_offset::Integer,
    memory_size::Integer;
    next
) -> Vulkan._BindVideoSessionMemoryInfoKHR

```
