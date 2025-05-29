拡張: VK*EXT*descriptor_buffer

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `info::_AccelerationStructureCaptureDescriptorDataInfoEXT`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetAccelerationStructureOpaqueCaptureDescriptorDataEXT.html)

```julia
_get_acceleration_structure_opaque_capture_descriptor_data_ext(
    device,
    info::Vulkan._AccelerationStructureCaptureDescriptorDataInfoEXT
) -> ResultTypes.Result{Ptr{Nothing}, Vulkan.VulkanError}

```
