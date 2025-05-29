引数:

  * `device::Device`
  * `info::ImageMemoryRequirementsInfo2`
  * `next_types::Type...`: `next` チェーンの一部として初期化し含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageMemoryRequirements2.html)

```julia
get_image_memory_requirements_2(
    device,
    info::Vulkan.ImageMemoryRequirementsInfo2,
    next_types::Type...
) -> Vulkan.MemoryRequirements2

```
