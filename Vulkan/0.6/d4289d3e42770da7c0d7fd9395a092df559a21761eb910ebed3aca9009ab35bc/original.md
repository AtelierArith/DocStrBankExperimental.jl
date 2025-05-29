Extension: VK_NV_optical_flow

Return codes:

  * `SUCCESS`
  * `ERROR_EXTENSION_NOT_PRESENT`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_FORMAT_NOT_SUPPORTED`

Arguments:

  * `physical_device::PhysicalDevice`
  * `optical_flow_image_format_info::OpticalFlowImageFormatInfoNV`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceOpticalFlowImageFormatsNV.html)

```julia
get_physical_device_optical_flow_image_formats_nv(
    physical_device,
    optical_flow_image_format_info::Vulkan.OpticalFlowImageFormatInfoNV
) -> ResultTypes.Result{Vector{Vulkan.OpticalFlowImageFormatPropertiesNV}, Vulkan.VulkanError}

```
