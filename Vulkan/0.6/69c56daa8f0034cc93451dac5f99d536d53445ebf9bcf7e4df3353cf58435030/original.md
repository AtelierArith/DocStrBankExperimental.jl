Arguments:

  * `device_indices::Vector{UInt32}`
  * `split_instance_bind_regions::Vector{Rect2D}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemoryDeviceGroupInfo.html)

```julia
BindImageMemoryDeviceGroupInfo(
    device_indices::AbstractArray,
    split_instance_bind_regions::AbstractArray;
    next
) -> Vulkan.BindImageMemoryDeviceGroupInfo

```
