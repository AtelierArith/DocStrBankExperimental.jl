引数:

  * `device::Device`
  * `pipeline_layout::PipelineLayout` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyPipelineLayout.html)

```julia
destroy_pipeline_layout(device, pipeline_layout; allocator)

```
