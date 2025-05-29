拡張: VK*KHR*ray*tracing*pipeline

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `raygen_shader_binding_table::_StridedDeviceAddressRegionKHR`
  * `miss_shader_binding_table::_StridedDeviceAddressRegionKHR`
  * `hit_shader_binding_table::_StridedDeviceAddressRegionKHR`
  * `callable_shader_binding_table::_StridedDeviceAddressRegionKHR`
  * `width::UInt32`
  * `height::UInt32`
  * `depth::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdTraceRaysKHR.html)

```julia
_cmd_trace_rays_khr(
    command_buffer,
    raygen_shader_binding_table::Vulkan._StridedDeviceAddressRegionKHR,
    miss_shader_binding_table::Vulkan._StridedDeviceAddressRegionKHR,
    hit_shader_binding_table::Vulkan._StridedDeviceAddressRegionKHR,
    callable_shader_binding_table::Vulkan._StridedDeviceAddressRegionKHR,
    width::Integer,
    height::Integer,
    depth::Integer
)

```
