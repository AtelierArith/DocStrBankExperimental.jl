Extension: VK_EXT_debug_marker

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `name_info::DebugMarkerObjectNameInfoEXT` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDebugMarkerSetObjectNameEXT.html)

```julia
debug_marker_set_object_name_ext(
    device,
    name_info::Vulkan.DebugMarkerObjectNameInfoEXT
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
