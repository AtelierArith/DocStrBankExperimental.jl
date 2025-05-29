Extension: VK_EXT_validation_cache

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `validation_cache::ValidationCacheEXT`

!!! warning
    The pointer returned by this function holds memory owned by Julia. It is therefore **your** responsibility to free it after use (e.g. with `Libc.free`).


[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetValidationCacheDataEXT.html)

```julia
get_validation_cache_data_ext(
    device,
    validation_cache
) -> ResultTypes.Result{Tuple{UInt64, Ptr{Nothing}}, Vulkan.VulkanError}

```
