拡張: VK*EXT*external*memory*host

引数:

  * `min_imported_host_pointer_alignment::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceExternalMemoryHostPropertiesEXT.html)

```julia
_PhysicalDeviceExternalMemoryHostPropertiesEXT(
    min_imported_host_pointer_alignment::Integer;
    next
) -> Vulkan._PhysicalDeviceExternalMemoryHostPropertiesEXT

```
