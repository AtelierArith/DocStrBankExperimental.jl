引数:

  * `device::Device`
  * `info::_ImageMemoryRequirementsInfo2`
  * `next_types::Type...`: `next` チェーンの一部として初期化し、含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageMemoryRequirements2.html)

```julia
_get_image_memory_requirements_2(
    device,
    info::Vulkan._ImageMemoryRequirementsInfo2,
    next_types::Type...
) -> Vulkan._MemoryRequirements2

```
