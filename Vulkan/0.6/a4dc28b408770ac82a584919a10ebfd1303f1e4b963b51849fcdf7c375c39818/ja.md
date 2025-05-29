引数:

  * `resource_device_index::UInt32`
  * `memory_device_index::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupBindSparseInfo.html)

```julia
_DeviceGroupBindSparseInfo(
    resource_device_index::Integer,
    memory_device_index::Integer;
    next
) -> Vulkan._DeviceGroupBindSparseInfo

```
