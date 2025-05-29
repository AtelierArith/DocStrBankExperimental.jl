Return codes:

  * `SUCCESS`
  * `PIPELINE_COMPILE_REQUIRED_EXT`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_SHADER_NV`

Arguments:

  * `device::Device`
  * `create_infos::Vector{ComputePipelineCreateInfo}`
  * `pipeline_cache::PipelineCache`: defaults to `C_NULL`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateComputePipelines.html)

```julia
create_compute_pipelines(
    device,
    create_infos::AbstractArray;
    pipeline_cache,
    allocator
) -> ResultTypes.Result{Tuple{Vector{Vulkan.Pipeline}, Vulkan.Result}, Vulkan.VulkanError}

```
