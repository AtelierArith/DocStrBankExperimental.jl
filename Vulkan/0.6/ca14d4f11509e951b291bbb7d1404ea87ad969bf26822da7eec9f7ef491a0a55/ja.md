引数:

  * `queue_family_index::UInt32`
  * `queue_index::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::DeviceQueueCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceQueueInfo2.html)

```julia
DeviceQueueInfo2(
    queue_family_index::Integer,
    queue_index::Integer;
    next,
    flags
) -> Vulkan.DeviceQueueInfo2

```
