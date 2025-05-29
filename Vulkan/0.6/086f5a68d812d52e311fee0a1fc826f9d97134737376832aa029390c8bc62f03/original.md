Extension: VK_EXT_debug_utils

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `name_info::DebugUtilsObjectNameInfoEXT` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSetDebugUtilsObjectNameEXT.html)

```julia
set_debug_utils_object_name_ext(
    device,
    name_info::Vulkan.DebugUtilsObjectNameInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
