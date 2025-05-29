Arguments:

  * `physical_device::PhysicalDevice`
  * `queue_create_infos::Vector{DeviceQueueCreateInfo}`
  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `enabled_features::PhysicalDeviceFeatures`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDevice.html)

```julia
Device(
    physical_device,
    queue_create_infos::AbstractArray,
    enabled_layer_names::AbstractArray,
    enabled_extension_names::AbstractArray;
    allocator,
    next,
    flags,
    enabled_features
) -> Vulkan.Device

```
