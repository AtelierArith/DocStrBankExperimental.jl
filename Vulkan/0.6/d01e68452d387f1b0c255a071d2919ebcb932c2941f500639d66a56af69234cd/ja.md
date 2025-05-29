引数:

  * `device_indices::Vector{UInt32}`
  * `split_instance_bind_regions::Vector{_Rect2D}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemoryDeviceGroupInfo.html)

```julia
_BindImageMemoryDeviceGroupInfo(
    device_indices::AbstractArray,
    split_instance_bind_regions::AbstractArray;
    next
) -> Vulkan._BindImageMemoryDeviceGroupInfo

```
