引数:

  * `device::Device`
  * `info::DeviceBufferMemoryRequirements`
  * `next_types::Type...`: `next` チェーンの一部として初期化し含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceBufferMemoryRequirements.html)

```julia
get_device_buffer_memory_requirements(
    device,
    info::Vulkan.DeviceBufferMemoryRequirements,
    next_types::Type...
) -> Vulkan.MemoryRequirements2

```
