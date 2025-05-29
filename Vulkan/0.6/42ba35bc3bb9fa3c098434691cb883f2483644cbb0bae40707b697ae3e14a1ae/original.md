Extension: VK_EXT_validation_cache

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `dst_cache::ValidationCacheEXT` (externsync)
  * `src_caches::Vector{ValidationCacheEXT}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkMergeValidationCachesEXT.html)

```julia
merge_validation_caches_ext(
    device,
    dst_cache,
    src_caches::AbstractArray
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
