Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `set_layouts::Vector{DescriptorSetLayout}`
  * `push_constant_ranges::Vector{_PushConstantRange}`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::PipelineLayoutCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreatePipelineLayout.html)

```julia
_create_pipeline_layout(
    device,
    set_layouts::AbstractArray,
    push_constant_ranges::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.PipelineLayout, Vulkan.VulkanError}

```
