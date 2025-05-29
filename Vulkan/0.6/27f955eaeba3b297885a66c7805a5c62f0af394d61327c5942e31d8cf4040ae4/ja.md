高レベルラッパー VkDecompressMemoryRegionNV。

拡張: VK*NV*memory_decompression

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDecompressMemoryRegionNV.html)

```julia
struct DecompressMemoryRegionNV <: Vulkan.HighLevelStruct
```

  * `src_address::UInt64`
  * `dst_address::UInt64`
  * `compressed_size::UInt64`
  * `decompressed_size::UInt64`
  * `decompression_method::UInt64`
