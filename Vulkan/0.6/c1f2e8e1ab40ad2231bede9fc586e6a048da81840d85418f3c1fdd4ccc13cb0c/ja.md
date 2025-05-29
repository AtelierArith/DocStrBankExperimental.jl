引数:

  * `device::Device`
  * `pipeline_cache::PipelineCache` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyPipelineCache.html)

```julia
destroy_pipeline_cache(device, pipeline_cache; allocator)

```
