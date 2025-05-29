拡張: VK*KHR*ray*tracing*pipeline

引数:

  * `stride::UInt64`
  * `size::UInt64`
  * `device_address::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkStridedDeviceAddressRegionKHR.html)

```julia
StridedDeviceAddressRegionKHR(
    stride::Integer,
    size::Integer;
    device_address
) -> Vulkan.StridedDeviceAddressRegionKHR

```
