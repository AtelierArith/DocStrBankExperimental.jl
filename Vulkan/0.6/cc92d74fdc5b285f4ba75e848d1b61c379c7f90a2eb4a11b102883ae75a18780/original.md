Arguments:

  * `handle_type::ExternalSemaphoreHandleTypeFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceExternalSemaphoreInfo.html)

```julia
_PhysicalDeviceExternalSemaphoreInfo(
    handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag;
    next
) -> Vulkan._PhysicalDeviceExternalSemaphoreInfo

```
