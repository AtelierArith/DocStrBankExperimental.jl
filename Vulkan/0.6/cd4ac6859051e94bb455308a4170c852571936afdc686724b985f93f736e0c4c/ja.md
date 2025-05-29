引数:

  * `usage::BufferUsageFlag`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::BufferCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceExternalBufferInfo.html)

```julia
PhysicalDeviceExternalBufferInfo(
    usage::Vulkan.BufferUsageFlag,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag;
    next,
    flags
) -> Vulkan.PhysicalDeviceExternalBufferInfo

```
