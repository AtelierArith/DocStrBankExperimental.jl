拡張機能: VK*EXT*debug_utils

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `name_info::_DebugUtilsObjectNameInfoEXT` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSetDebugUtilsObjectNameEXT.html)

```julia
_set_debug_utils_object_name_ext(
    device,
    name_info::Vulkan._DebugUtilsObjectNameInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
