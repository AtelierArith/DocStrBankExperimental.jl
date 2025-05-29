拡張: VK*KHR*video_queue

引数:

  * `memory_bind_index::UInt32`
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`
  * `memory_size::UInt64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindVideoSessionMemoryInfoKHR.html)

```julia
BindVideoSessionMemoryInfoKHR(
    memory_bind_index::Integer,
    memory::Vulkan.DeviceMemory,
    memory_offset::Integer,
    memory_size::Integer;
    next
) -> Vulkan.BindVideoSessionMemoryInfoKHR

```
