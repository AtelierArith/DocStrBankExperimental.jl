引数:

  * `device_indices::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindBufferMemoryDeviceGroupInfo.html)

```julia
BindBufferMemoryDeviceGroupInfo(
    device_indices::AbstractArray;
    next
) -> Vulkan.BindBufferMemoryDeviceGroupInfo

```
