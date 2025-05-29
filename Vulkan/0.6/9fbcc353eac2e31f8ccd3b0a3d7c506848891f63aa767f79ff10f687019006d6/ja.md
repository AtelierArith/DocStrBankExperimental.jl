引数:

  * `queue_count::UInt32`
  * `timestamp_valid_bits::UInt32`
  * `min_image_transfer_granularity::Extent3D`
  * `queue_flags::QueueFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyProperties.html)

```julia
QueueFamilyProperties(
    queue_count::Integer,
    timestamp_valid_bits::Integer,
    min_image_transfer_granularity::Vulkan.Extent3D;
    queue_flags
) -> Vulkan.QueueFamilyProperties

```
