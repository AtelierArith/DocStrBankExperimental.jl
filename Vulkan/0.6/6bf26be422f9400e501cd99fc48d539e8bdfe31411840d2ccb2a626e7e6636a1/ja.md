拡張: VK*EXT*validation_cache

引数:

  * `device::Device`
  * `validation_cache::ValidationCacheEXT` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyValidationCacheEXT.html)

```julia
destroy_validation_cache_ext(
    device,
    validation_cache;
    allocator
)

```
