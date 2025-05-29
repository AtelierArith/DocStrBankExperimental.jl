拡張: VK*EXT*debug_marker

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `name_info::_DebugMarkerObjectNameInfoEXT` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDebugMarkerSetObjectNameEXT.html)

```julia
_debug_marker_set_object_name_ext(
    device,
    name_info::Vulkan._DebugMarkerObjectNameInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
