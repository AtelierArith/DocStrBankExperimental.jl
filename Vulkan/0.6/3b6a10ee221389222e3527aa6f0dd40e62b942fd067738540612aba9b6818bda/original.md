Extension: VK_KHR_ray_tracing_pipeline

Return codes:

  * `SUCCESS`
  * `OPERATION_DEFERRED_KHR`
  * `OPERATION_NOT_DEFERRED_KHR`
  * `PIPELINE_COMPILE_REQUIRED_EXT`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS`

Arguments:

  * `device::Device`
  * `create_infos::Vector{RayTracingPipelineCreateInfoKHR}`
  * `deferred_operation::DeferredOperationKHR`: defaults to `C_NULL`
  * `pipeline_cache::PipelineCache`: defaults to `C_NULL`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRayTracingPipelinesKHR.html)

```julia
create_ray_tracing_pipelines_khr(
    device,
    create_infos::AbstractArray;
    deferred_operation,
    pipeline_cache,
    allocator
) -> ResultTypes.Result{Tuple{Vector{Vulkan.Pipeline}, Vulkan.Result}, Vulkan.VulkanError}

```
