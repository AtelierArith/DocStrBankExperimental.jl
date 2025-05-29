Extension: VK_EXT_descriptor_buffer

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `info::_AccelerationStructureCaptureDescriptorDataInfoEXT`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetAccelerationStructureOpaqueCaptureDescriptorDataEXT.html)

```julia
_get_acceleration_structure_opaque_capture_descriptor_data_ext(
    device,
    info::Vulkan._AccelerationStructureCaptureDescriptorDataInfoEXT
) -> ResultTypes.Result{Ptr{Nothing}, Vulkan.VulkanError}

```
