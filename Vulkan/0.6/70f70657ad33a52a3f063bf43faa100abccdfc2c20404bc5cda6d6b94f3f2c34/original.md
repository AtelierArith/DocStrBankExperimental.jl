Arguments:

  * `device_indices::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindBufferMemoryDeviceGroupInfo.html)

```julia
_BindBufferMemoryDeviceGroupInfo(
    device_indices::AbstractArray;
    next
) -> Vulkan._BindBufferMemoryDeviceGroupInfo

```
