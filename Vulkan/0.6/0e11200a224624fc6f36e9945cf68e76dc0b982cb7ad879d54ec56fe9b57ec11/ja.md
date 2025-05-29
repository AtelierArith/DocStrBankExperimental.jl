拡張: VK*KHR*ray*tracing*pipeline

戻りコード:

  * `SUCCESS`
  * `OPERATION_DEFERRED_KHR`
  * `OPERATION_NOT_DEFERRED_KHR`
  * `PIPELINE_COMPILE_REQUIRED_EXT`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS`

引数:

  * `device::Device`
  * `create_infos::Vector{_RayTracingPipelineCreateInfoKHR}`
  * `deferred_operation::DeferredOperationKHR`: デフォルトは `C_NULL`
  * `pipeline_cache::PipelineCache`: デフォルトは `C_NULL`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRayTracingPipelinesKHR.html)

```julia
_create_ray_tracing_pipelines_khr(
    device,
    create_infos::AbstractArray;
    deferred_operation,
    pipeline_cache,
    allocator
) -> ResultTypes.Result{Tuple{Vector{Vulkan.Pipeline}, Vulkan.Result}, Vulkan.VulkanError}

```
