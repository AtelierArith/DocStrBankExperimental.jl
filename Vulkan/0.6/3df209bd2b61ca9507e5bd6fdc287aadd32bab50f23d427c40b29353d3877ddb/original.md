Extension: VK_EXT_debug_utils

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `tag_info::_DebugUtilsObjectTagInfoEXT` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSetDebugUtilsObjectTagEXT.html)

```julia
_set_debug_utils_object_tag_ext(
    device,
    tag_info::Vulkan._DebugUtilsObjectTagInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
