Arguments:

  * `physical_device_count::UInt32`
  * `physical_devices::NTuple{Int(VK_MAX_DEVICE_GROUP_SIZE), PhysicalDevice}`
  * `subset_allocation::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceGroupProperties.html)

```julia
PhysicalDeviceGroupProperties(
    physical_device_count::Integer,
    physical_devices::NTuple{32, Vulkan.PhysicalDevice},
    subset_allocation::Bool;
    next
) -> Vulkan.PhysicalDeviceGroupProperties

```
