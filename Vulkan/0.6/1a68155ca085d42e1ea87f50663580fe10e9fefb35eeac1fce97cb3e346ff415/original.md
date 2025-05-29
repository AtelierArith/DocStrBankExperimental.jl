Extension: VK_NV_ray_tracing

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `pipeline::Pipeline`
  * `shader::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCompileDeferredNV.html)

```julia
_compile_deferred_nv(
    device,
    pipeline,
    shader::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
