Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `pipeline_cache::PipelineCache`

!!! warning
    The pointer returned by this function holds memory owned by Julia. It is therefore **your** responsibility to free it after use (e.g. with `Libc.free`).


[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPipelineCacheData.html)

```julia
get_pipeline_cache_data(
    device,
    pipeline_cache
) -> ResultTypes.Result{Tuple{UInt64, Ptr{Nothing}}, Vulkan.VulkanError}

```
