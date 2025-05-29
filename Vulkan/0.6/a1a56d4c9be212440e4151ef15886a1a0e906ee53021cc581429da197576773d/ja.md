拡張: VK*EXT*debug_utils

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `tag_info::DebugUtilsObjectTagInfoEXT` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSetDebugUtilsObjectTagEXT.html)

```julia
set_debug_utils_object_tag_ext(
    device,
    tag_info::Vulkan.DebugUtilsObjectTagInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
