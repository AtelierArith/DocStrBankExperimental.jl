拡張: VK*EXT*pipeline_properties

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `pipeline_info::VkPipelineInfoEXT`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPipelinePropertiesEXT.html)

```julia
get_pipeline_properties_ext(
    device,
    pipeline_info::VulkanCore.LibVulkan.VkPipelineInfoKHR
) -> ResultTypes.Result{Vulkan.BaseOutStructure, Vulkan.VulkanError}

```
