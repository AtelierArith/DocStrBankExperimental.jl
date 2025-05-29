Extension: VK_NV_memory_decompression

Arguments:

  * `src_address::UInt64`
  * `dst_address::UInt64`
  * `compressed_size::UInt64`
  * `decompressed_size::UInt64`
  * `decompression_method::UInt64`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDecompressMemoryRegionNV.html)

```julia
_DecompressMemoryRegionNV(
    src_address::Integer,
    dst_address::Integer,
    compressed_size::Integer,
    decompressed_size::Integer,
    decompression_method::Integer
) -> Vulkan._DecompressMemoryRegionNV

```
