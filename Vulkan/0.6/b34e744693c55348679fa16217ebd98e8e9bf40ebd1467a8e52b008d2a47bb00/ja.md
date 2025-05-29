拡張: VK*EXT*descriptor_buffer

戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `info::_ImageCaptureDescriptorDataInfoEXT`

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageOpaqueCaptureDescriptorDataEXT.html)

```julia
_get_image_opaque_capture_descriptor_data_ext(
    device,
    info::Vulkan._ImageCaptureDescriptorDataInfoEXT
) -> ResultTypes.Result{Ptr{Nothing}, Vulkan.VulkanError}

```
