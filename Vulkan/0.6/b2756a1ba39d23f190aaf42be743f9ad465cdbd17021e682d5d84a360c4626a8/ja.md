拡張: VK*EXT*validation_cache

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `initial_data::Ptr{Cvoid}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `initial_data_size::UInt`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateValidationCacheEXT.html)

```julia
_create_validation_cache_ext(
    device,
    initial_data::Ptr{Nothing};
    allocator,
    next,
    flags,
    initial_data_size
) -> ResultTypes.Result{Vulkan.ValidationCacheEXT, Vulkan.VulkanError}

```
