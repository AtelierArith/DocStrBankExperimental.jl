拡張: VK*KHR*external*memory*fd

引数:

  * `memory_type_bits::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryFdPropertiesKHR.html)

```julia
_MemoryFdPropertiesKHR(
    memory_type_bits::Integer;
    next
) -> Vulkan._MemoryFdPropertiesKHR

```
