Arguments:

  * `queue_create_infos::Vector{_DeviceQueueCreateInfo}`
  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `enabled_features::_PhysicalDeviceFeatures`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceCreateInfo.html)

```julia
_DeviceCreateInfo(
    queue_create_infos::AbstractArray,
    enabled_layer_names::AbstractArray,
    enabled_extension_names::AbstractArray;
    next,
    flags,
    enabled_features
) -> Vulkan._DeviceCreateInfo

```
