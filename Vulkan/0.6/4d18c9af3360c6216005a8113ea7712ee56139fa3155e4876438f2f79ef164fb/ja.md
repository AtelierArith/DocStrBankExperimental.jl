拡張: VK*EXT*debug_marker

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `tag_info::DebugMarkerObjectTagInfoEXT` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDebugMarkerSetObjectTagEXT.html)

```julia
debug_marker_set_object_tag_ext(
    device,
    tag_info::Vulkan.DebugMarkerObjectTagInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
