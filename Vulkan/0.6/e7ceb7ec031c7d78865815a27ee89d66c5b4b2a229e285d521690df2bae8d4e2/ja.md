引数:

  * `queue_create_infos::Vector{DeviceQueueCreateInfo}`
  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `enabled_features::PhysicalDeviceFeatures`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceCreateInfo.html)

```julia
DeviceCreateInfo(
    queue_create_infos::AbstractArray,
    enabled_layer_names::AbstractArray,
    enabled_extension_names::AbstractArray;
    next,
    flags,
    enabled_features
) -> Vulkan.DeviceCreateInfo

```
