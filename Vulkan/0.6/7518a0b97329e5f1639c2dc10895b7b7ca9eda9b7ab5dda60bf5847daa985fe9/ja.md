拡張: VK*KHR*external*memory*fd

引数:

  * `memory::DeviceMemory`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetFdInfoKHR.html)

```julia
MemoryGetFdInfoKHR(
    memory::Vulkan.DeviceMemory,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag;
    next
) -> Vulkan.MemoryGetFdInfoKHR

```
