拡張: VK*NV*device*generated*commands

引数:

  * `device::Device`
  * `info::GeneratedCommandsMemoryRequirementsInfoNV`
  * `next_types::Type...`: `next` チェーンの一部として初期化し、含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetGeneratedCommandsMemoryRequirementsNV.html)

```julia
get_generated_commands_memory_requirements_nv(
    device,
    info::Vulkan.GeneratedCommandsMemoryRequirementsInfoNV,
    next_types::Type...
) -> Vulkan.MemoryRequirements2

```
