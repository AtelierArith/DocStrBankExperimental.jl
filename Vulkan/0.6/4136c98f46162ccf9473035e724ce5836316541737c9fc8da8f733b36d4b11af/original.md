Arguments:

  * `device_indices::Vector{UInt32}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindBufferMemoryDeviceGroupInfo.html)

```julia
BindBufferMemoryDeviceGroupInfo(
    device_indices::AbstractArray;
    next
) -> Vulkan.BindBufferMemoryDeviceGroupInfo

```
