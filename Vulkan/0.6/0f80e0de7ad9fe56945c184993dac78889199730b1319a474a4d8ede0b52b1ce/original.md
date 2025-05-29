Extension: VK_EXT_descriptor_buffer

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `info::SamplerCaptureDescriptorDataInfoEXT`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetSamplerOpaqueCaptureDescriptorDataEXT.html)

```julia
get_sampler_opaque_capture_descriptor_data_ext(
    device,
    info::Vulkan.SamplerCaptureDescriptorDataInfoEXT
) -> ResultTypes.Result{Ptr{Nothing}, Vulkan.VulkanError}

```
