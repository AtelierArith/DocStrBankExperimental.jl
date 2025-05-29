Extension: VK_EXT_descriptor_buffer

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `info::_ImageViewCaptureDescriptorDataInfoEXT`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageViewOpaqueCaptureDescriptorDataEXT.html)

```julia
_get_image_view_opaque_capture_descriptor_data_ext(
    device,
    info::Vulkan._ImageViewCaptureDescriptorDataInfoEXT
) -> ResultTypes.Result{Ptr{Nothing}, Vulkan.VulkanError}

```
