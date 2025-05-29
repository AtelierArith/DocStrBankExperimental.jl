引数:

  * `device::Device`
  * `info::DeviceImageMemoryRequirements`
  * `next_types::Type...`: `next` チェーンの一部として初期化し含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceImageMemoryRequirements.html)

```julia
get_device_image_memory_requirements(
    device,
    info::Vulkan.DeviceImageMemoryRequirements,
    next_types::Type...
) -> Vulkan.MemoryRequirements2

```
