Extension: VK_NV_memory_decompression

Arguments:

  * `decompression_methods::UInt64`
  * `max_decompression_indirect_count::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryDecompressionPropertiesNV.html)

```julia
PhysicalDeviceMemoryDecompressionPropertiesNV(
    decompression_methods::Integer,
    max_decompression_indirect_count::Integer;
    next
) -> Vulkan.PhysicalDeviceMemoryDecompressionPropertiesNV

```
