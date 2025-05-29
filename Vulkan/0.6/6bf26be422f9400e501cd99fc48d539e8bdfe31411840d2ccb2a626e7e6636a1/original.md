Extension: VK_EXT_validation_cache

Arguments:

  * `device::Device`
  * `validation_cache::ValidationCacheEXT` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyValidationCacheEXT.html)

```julia
destroy_validation_cache_ext(
    device,
    validation_cache;
    allocator
)

```
