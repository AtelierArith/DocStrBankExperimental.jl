Extension: VK_KHR_external_memory_fd

Arguments:

  * `memory_type_bits::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryFdPropertiesKHR.html)

```julia
_MemoryFdPropertiesKHR(
    memory_type_bits::Integer;
    next
) -> Vulkan._MemoryFdPropertiesKHR

```
