拡張: VK*NV*memory_decompression

引数:

  * `decompression_methods::UInt64`
  * `max_decompression_indirect_count::UInt64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryDecompressionPropertiesNV.html)

```julia
PhysicalDeviceMemoryDecompressionPropertiesNV(
    decompression_methods::Integer,
    max_decompression_indirect_count::Integer;
    next
) -> Vulkan.PhysicalDeviceMemoryDecompressionPropertiesNV

```
