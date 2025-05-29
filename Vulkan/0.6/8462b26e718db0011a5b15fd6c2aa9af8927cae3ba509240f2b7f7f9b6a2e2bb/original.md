Arguments:

  * `device::Device`
  * `info::_DeviceBufferMemoryRequirements`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceBufferMemoryRequirements.html)

```julia
_get_device_buffer_memory_requirements(
    device,
    info::Vulkan._DeviceBufferMemoryRequirements,
    next_types::Type...
) -> Vulkan._MemoryRequirements2

```
