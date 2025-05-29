引数:

  * `device::Device`
  * `pipeline_layout::PipelineLayout` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyPipelineLayout.html)

```julia
_destroy_pipeline_layout(device, pipeline_layout; allocator)

```
