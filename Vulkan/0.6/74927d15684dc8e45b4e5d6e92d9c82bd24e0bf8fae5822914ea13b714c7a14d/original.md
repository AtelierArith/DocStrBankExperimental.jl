Extension: VK_EXT_robustness2

Arguments:

  * `robust_storage_buffer_access_size_alignment::UInt64`
  * `robust_uniform_buffer_access_size_alignment::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRobustness2PropertiesEXT.html)

```julia
PhysicalDeviceRobustness2PropertiesEXT(
    robust_storage_buffer_access_size_alignment::Integer,
    robust_uniform_buffer_access_size_alignment::Integer;
    next
) -> Vulkan.PhysicalDeviceRobustness2PropertiesEXT

```
