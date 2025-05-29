引数:

  * `handle_type::ExternalFenceHandleTypeFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceExternalFenceInfo.html)

```julia
_PhysicalDeviceExternalFenceInfo(
    handle_type::Vulkan.ExternalFenceHandleTypeFlag;
    next
) -> Vulkan._PhysicalDeviceExternalFenceInfo

```
