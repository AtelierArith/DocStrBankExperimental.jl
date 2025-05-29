Extension: VK_KHR_external_memory_fd

Arguments:

  * `memory::DeviceMemory`
  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetFdInfoKHR.html)

```julia
_MemoryGetFdInfoKHR(
    memory,
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag;
    next
) -> Vulkan._MemoryGetFdInfoKHR

```
