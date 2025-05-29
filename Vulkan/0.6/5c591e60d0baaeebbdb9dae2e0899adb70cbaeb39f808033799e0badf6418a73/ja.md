拡張: VK*EXT*robustness2

引数:

  * `robust_storage_buffer_access_size_alignment::UInt64`
  * `robust_uniform_buffer_access_size_alignment::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRobustness2PropertiesEXT.html)

```julia
_PhysicalDeviceRobustness2PropertiesEXT(
    robust_storage_buffer_access_size_alignment::Integer,
    robust_uniform_buffer_access_size_alignment::Integer;
    next
) -> Vulkan._PhysicalDeviceRobustness2PropertiesEXT

```
