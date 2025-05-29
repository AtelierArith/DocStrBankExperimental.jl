引数:

  * `device::Device`
  * `pipeline_cache::PipelineCache` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyPipelineCache.html)

```julia
_destroy_pipeline_cache(device, pipeline_cache; allocator)

```
