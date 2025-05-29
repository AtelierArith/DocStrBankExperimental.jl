Arguments:

  * `buffer::Buffer`
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindBufferMemoryInfo.html)

```julia
BindBufferMemoryInfo(
    buffer::Vulkan.Buffer,
    memory::Vulkan.DeviceMemory,
    memory_offset::Integer;
    next
) -> Vulkan.BindBufferMemoryInfo

```
