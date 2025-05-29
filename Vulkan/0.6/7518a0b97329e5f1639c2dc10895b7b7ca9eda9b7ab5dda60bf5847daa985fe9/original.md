Extension: VK_KHR_external_memory_fd

Arguments:

  * `memory::DeviceMemory`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetFdInfoKHR.html)

```julia
MemoryGetFdInfoKHR(
    memory::Vulkan.DeviceMemory,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag;
    next
) -> Vulkan.MemoryGetFdInfoKHR

```
