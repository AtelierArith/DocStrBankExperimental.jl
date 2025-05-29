引数:

  * `device_mask::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupCommandBufferBeginInfo.html)

```julia
_DeviceGroupCommandBufferBeginInfo(
    device_mask::Integer;
    next
) -> Vulkan._DeviceGroupCommandBufferBeginInfo

```
