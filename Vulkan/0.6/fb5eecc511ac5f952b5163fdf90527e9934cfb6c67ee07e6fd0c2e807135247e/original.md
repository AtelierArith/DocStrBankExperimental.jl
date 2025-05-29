Arguments:

  * `device::Device`
  * `info::DeviceImageMemoryRequirements`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceImageMemoryRequirements.html)

```julia
get_device_image_memory_requirements(
    device,
    info::Vulkan.DeviceImageMemoryRequirements,
    next_types::Type...
) -> Vulkan.MemoryRequirements2

```
