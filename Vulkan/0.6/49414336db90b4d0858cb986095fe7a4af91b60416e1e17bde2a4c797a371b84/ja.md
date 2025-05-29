戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `set_layouts::Vector{DescriptorSetLayout}`
  * `push_constant_ranges::Vector{PushConstantRange}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::PipelineLayoutCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePipelineLayout.html)

```julia
create_pipeline_layout(
    device,
    set_layouts::AbstractArray,
    push_constant_ranges::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.PipelineLayout, Vulkan.VulkanError}

```
