引数:

  * `image::Image`
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemoryInfo.html)

```julia
BindImageMemoryInfo(
    image::Vulkan.Image,
    memory::Vulkan.DeviceMemory,
    memory_offset::Integer;
    next
) -> Vulkan.BindImageMemoryInfo

```
