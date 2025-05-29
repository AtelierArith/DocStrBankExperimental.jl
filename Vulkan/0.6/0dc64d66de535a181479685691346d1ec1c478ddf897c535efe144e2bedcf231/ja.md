拡張: VK*EXT*validation_cache

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `create_info::ValidationCacheCreateInfoEXT`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateValidationCacheEXT.html)

```julia
create_validation_cache_ext(
    device,
    create_info::Vulkan.ValidationCacheCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.ValidationCacheEXT, Vulkan.VulkanError}

```
