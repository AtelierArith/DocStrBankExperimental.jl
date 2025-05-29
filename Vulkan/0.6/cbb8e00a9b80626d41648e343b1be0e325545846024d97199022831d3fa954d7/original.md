Extension: VK_EXT_pipeline_properties

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `pipeline_info::VkPipelineInfoEXT`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPipelinePropertiesEXT.html)

```julia
_get_pipeline_properties_ext(
    device,
    pipeline_info::VulkanCore.LibVulkan.VkPipelineInfoKHR
) -> ResultTypes.Result{Vulkan._BaseOutStructure, Vulkan.VulkanError}

```
