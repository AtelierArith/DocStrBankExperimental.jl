Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `dst_cache::PipelineCache` (externsync)
  * `src_caches::Vector{PipelineCache}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkMergePipelineCaches.html)

```julia
_merge_pipeline_caches(
    device,
    dst_cache,
    src_caches::AbstractArray
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
