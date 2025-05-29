拡張: VK*EXT*validation_cache

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `dst_cache::ValidationCacheEXT` (externsync)
  * `src_caches::Vector{ValidationCacheEXT}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkMergeValidationCachesEXT.html)

```julia
_merge_validation_caches_ext(
    device,
    dst_cache,
    src_caches::AbstractArray
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
