High-level wrapper for VkDecompressMemoryRegionNV.

Extension: VK_NV_memory_decompression

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDecompressMemoryRegionNV.html)

```julia
struct DecompressMemoryRegionNV <: Vulkan.HighLevelStruct
```

  * `src_address::UInt64`
  * `dst_address::UInt64`
  * `compressed_size::UInt64`
  * `decompressed_size::UInt64`
  * `decompression_method::UInt64`
