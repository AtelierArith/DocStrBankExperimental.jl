引数:

  * `physical_device::PhysicalDevice`
  * `queue_create_infos::Vector{_DeviceQueueCreateInfo}`
  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `enabled_features::_PhysicalDeviceFeatures`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDevice.html)

```julia
Device(
    physical_device,
    queue_create_infos::AbstractArray{Vulkan._DeviceQueueCreateInfo},
    enabled_layer_names::AbstractArray,
    enabled_extension_names::AbstractArray;
    allocator,
    next,
    flags,
    enabled_features
) -> Vulkan.Device

```
