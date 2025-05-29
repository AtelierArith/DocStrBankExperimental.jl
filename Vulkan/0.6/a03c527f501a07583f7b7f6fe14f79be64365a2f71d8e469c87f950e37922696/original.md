Arguments:

  * `device::Device`
  * `info::_ImageMemoryRequirementsInfo2`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageMemoryRequirements2.html)

```julia
_get_image_memory_requirements_2(
    device,
    info::Vulkan._ImageMemoryRequirementsInfo2,
    next_types::Type...
) -> Vulkan._MemoryRequirements2

```
