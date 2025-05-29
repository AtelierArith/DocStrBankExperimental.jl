戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::PipelineLayoutCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePipelineLayout.html)

```julia
create_pipeline_layout(
    device,
    create_info::Vulkan.PipelineLayoutCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.PipelineLayout, Vulkan.VulkanError}

```
