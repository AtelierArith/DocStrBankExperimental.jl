Arguments:

  * `device::Device`
  * `info::DeviceBufferMemoryRequirements`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceBufferMemoryRequirements.html)

```julia
get_device_buffer_memory_requirements(
    device,
    info::Vulkan.DeviceBufferMemoryRequirements,
    next_types::Type...
) -> Vulkan.MemoryRequirements2

```
