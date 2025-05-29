Extension: VK_KHR_pipeline_executable_properties

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `executable_info::PipelineExecutableInfoKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPipelineExecutableInternalRepresentationsKHR.html)

```julia
get_pipeline_executable_internal_representations_khr(
    device,
    executable_info::Vulkan.PipelineExecutableInfoKHR
) -> ResultTypes.Result{Vector{Vulkan.PipelineExecutableInternalRepresentationKHR}, Vulkan.VulkanError}

```
