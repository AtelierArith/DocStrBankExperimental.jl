Arguments:

  * `physical_device::PhysicalDevice`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceFeatures2.html)

```julia
get_physical_device_features_2(
    physical_device,
    next_types::Type...
) -> Vulkan.PhysicalDeviceFeatures2

```
