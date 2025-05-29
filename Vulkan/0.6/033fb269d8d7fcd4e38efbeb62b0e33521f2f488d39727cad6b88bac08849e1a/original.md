Extension: VK_KHR_ray_tracing_pipeline

Arguments:

  * `stride::UInt64`
  * `size::UInt64`
  * `device_address::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkStridedDeviceAddressRegionKHR.html)

```julia
_StridedDeviceAddressRegionKHR(
    stride::Integer,
    size::Integer;
    device_address
) -> Vulkan._StridedDeviceAddressRegionKHR

```
