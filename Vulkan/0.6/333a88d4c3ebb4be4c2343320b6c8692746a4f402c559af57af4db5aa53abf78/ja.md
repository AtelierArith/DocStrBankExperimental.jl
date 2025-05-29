拡張: VK*NV*device*generated*commands

引数:

  * `device::Device`
  * `info::_GeneratedCommandsMemoryRequirementsInfoNV`
  * `next_types::Type...`: `next` チェーンの一部として初期化し含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetGeneratedCommandsMemoryRequirementsNV.html)

```julia
_get_generated_commands_memory_requirements_nv(
    device,
    info::Vulkan._GeneratedCommandsMemoryRequirementsInfoNV,
    next_types::Type...
) -> Vulkan._MemoryRequirements2

```
