Arguments:

  * `device_indices::Vector{UInt32}`
  * `split_instance_bind_regions::Vector{_Rect2D}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemoryDeviceGroupInfo.html)

```julia
_BindImageMemoryDeviceGroupInfo(
    device_indices::AbstractArray,
    split_instance_bind_regions::AbstractArray;
    next
) -> Vulkan._BindImageMemoryDeviceGroupInfo

```
