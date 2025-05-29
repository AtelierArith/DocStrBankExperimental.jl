Extension: VK_KHR_pipeline_executable_properties

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `pipeline_info::_PipelineInfoKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPipelineExecutablePropertiesKHR.html)

```julia
_get_pipeline_executable_properties_khr(
    device,
    pipeline_info::Vulkan._PipelineInfoKHR
) -> ResultTypes.Result{Vector{Vulkan._PipelineExecutablePropertiesKHR}, Vulkan.VulkanError}

```
