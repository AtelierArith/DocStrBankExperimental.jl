Arguments:

  * `image::Image`
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemoryInfo.html)

```julia
_BindImageMemoryInfo(
    image,
    memory,
    memory_offset::Integer;
    next
) -> Vulkan._BindImageMemoryInfo

```
