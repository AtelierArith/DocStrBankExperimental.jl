Extension: VK_NV_ray_tracing

Return codes:

  * `SUCCESS`
  * `PIPELINE_COMPILE_REQUIRED_EXT`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_SHADER_NV`

Arguments:

  * `device::Device`
  * `create_infos::Vector{RayTracingPipelineCreateInfoNV}`
  * `pipeline_cache::PipelineCache`: defaults to `C_NULL`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRayTracingPipelinesNV.html)

```julia
create_ray_tracing_pipelines_nv(
    device,
    create_infos::AbstractArray;
    pipeline_cache,
    allocator
) -> ResultTypes.Result{Tuple{Vector{Vulkan.Pipeline}, Vulkan.Result}, Vulkan.VulkanError}

```
