Extension: VK_KHR_video_queue

Arguments:

  * `memory_bind_index::UInt32`
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`
  * `memory_size::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindVideoSessionMemoryInfoKHR.html)

```julia
BindVideoSessionMemoryInfoKHR(
    memory_bind_index::Integer,
    memory::Vulkan.DeviceMemory,
    memory_offset::Integer,
    memory_size::Integer;
    next
) -> Vulkan.BindVideoSessionMemoryInfoKHR

```
