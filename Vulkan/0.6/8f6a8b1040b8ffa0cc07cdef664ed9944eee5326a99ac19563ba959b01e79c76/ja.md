拡張: VK*KHR*ray*tracing*pipeline

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `raygen_shader_binding_table::StridedDeviceAddressRegionKHR`
  * `miss_shader_binding_table::StridedDeviceAddressRegionKHR`
  * `hit_shader_binding_table::StridedDeviceAddressRegionKHR`
  * `callable_shader_binding_table::StridedDeviceAddressRegionKHR`
  * `indirect_device_address::UInt64`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdTraceRaysIndirectKHR.html)

```julia
cmd_trace_rays_indirect_khr(
    command_buffer,
    raygen_shader_binding_table::Vulkan.StridedDeviceAddressRegionKHR,
    miss_shader_binding_table::Vulkan.StridedDeviceAddressRegionKHR,
    hit_shader_binding_table::Vulkan.StridedDeviceAddressRegionKHR,
    callable_shader_binding_table::Vulkan.StridedDeviceAddressRegionKHR,
    indirect_device_address::Integer
)

```
