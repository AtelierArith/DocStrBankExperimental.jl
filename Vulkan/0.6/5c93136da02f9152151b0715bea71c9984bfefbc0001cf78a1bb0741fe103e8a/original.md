Extension: VK_EXT_external_memory_host

Arguments:

  * `min_imported_host_pointer_alignment::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceExternalMemoryHostPropertiesEXT.html)

```julia
_PhysicalDeviceExternalMemoryHostPropertiesEXT(
    min_imported_host_pointer_alignment::Integer;
    next
) -> Vulkan._PhysicalDeviceExternalMemoryHostPropertiesEXT

```
