Arguments:

  * `queue_family_index::UInt32`
  * `queue_index::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::DeviceQueueCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceQueueInfo2.html)

```julia
_DeviceQueueInfo2(
    queue_family_index::Integer,
    queue_index::Integer;
    next,
    flags
) -> Vulkan._DeviceQueueInfo2

```
