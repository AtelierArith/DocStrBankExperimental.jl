引数:

  * `device::Device`
  * `info::_DeviceBufferMemoryRequirements`
  * `next_types::Type...`: `next` チェーンの一部として初期化し、含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceBufferMemoryRequirements.html)

```julia
_get_device_buffer_memory_requirements(
    device,
    info::Vulkan._DeviceBufferMemoryRequirements,
    next_types::Type...
) -> Vulkan._MemoryRequirements2

```
