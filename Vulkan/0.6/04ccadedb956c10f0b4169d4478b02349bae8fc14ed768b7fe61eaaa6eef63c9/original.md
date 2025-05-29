Extension: VK_KHR_ray_tracing_pipeline

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `pipeline::Pipeline`
  * `first_group::UInt32`
  * `group_count::UInt32`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}` (must be a valid pointer with `data_size` bytes)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetRayTracingCaptureReplayShaderGroupHandlesKHR.html)

```julia
_get_ray_tracing_capture_replay_shader_group_handles_khr(
    device,
    pipeline,
    first_group::Integer,
    group_count::Integer,
    data_size::Integer,
    data::Ptr{Nothing}
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
