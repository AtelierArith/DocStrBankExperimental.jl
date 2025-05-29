引数:

  * `memory_requirements::_MemoryRequirements`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryRequirements2.html)

```julia
_MemoryRequirements2(
    memory_requirements::Vulkan._MemoryRequirements;
    next
) -> Vulkan._MemoryRequirements2

```
