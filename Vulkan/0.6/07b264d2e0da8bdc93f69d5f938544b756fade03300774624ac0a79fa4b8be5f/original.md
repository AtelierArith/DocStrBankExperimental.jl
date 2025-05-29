Arguments:

  * `device::Device`
  * `info::BufferMemoryRequirementsInfo2`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetBufferMemoryRequirements2.html)

```julia
get_buffer_memory_requirements_2(
    device,
    info::Vulkan.BufferMemoryRequirementsInfo2,
    next_types::Type...
) -> Vulkan.MemoryRequirements2

```
