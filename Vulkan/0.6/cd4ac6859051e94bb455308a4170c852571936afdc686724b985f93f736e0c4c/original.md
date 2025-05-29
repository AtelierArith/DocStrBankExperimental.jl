Arguments:

  * `usage::BufferUsageFlag`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `next::Any`: defaults to `C_NULL`
  * `flags::BufferCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceExternalBufferInfo.html)

```julia
PhysicalDeviceExternalBufferInfo(
    usage::Vulkan.BufferUsageFlag,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag;
    next,
    flags
) -> Vulkan.PhysicalDeviceExternalBufferInfo

```
