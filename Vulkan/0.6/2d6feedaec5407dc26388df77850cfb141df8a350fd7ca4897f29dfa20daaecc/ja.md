引数:

  * `device::Device`
  * `info::_BufferMemoryRequirementsInfo2`
  * `next_types::Type...`: `next` チェーンの一部として初期化し含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetBufferMemoryRequirements2.html)

```julia
_get_buffer_memory_requirements_2(
    device,
    info::Vulkan._BufferMemoryRequirementsInfo2,
    next_types::Type...
) -> Vulkan._MemoryRequirements2

```
