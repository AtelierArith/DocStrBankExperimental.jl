Extension: VK_NV_device_generated_commands

Arguments:

  * `device::Device`
  * `info::GeneratedCommandsMemoryRequirementsInfoNV`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetGeneratedCommandsMemoryRequirementsNV.html)

```julia
get_generated_commands_memory_requirements_nv(
    device,
    info::Vulkan.GeneratedCommandsMemoryRequirementsInfoNV,
    next_types::Type...
) -> Vulkan.MemoryRequirements2

```
