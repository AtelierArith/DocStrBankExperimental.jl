引数:

  * `memory_requirements::_SparseImageMemoryRequirements`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryRequirements2.html)

```julia
_SparseImageMemoryRequirements2(
    memory_requirements::Vulkan._SparseImageMemoryRequirements;
    next
) -> Vulkan._SparseImageMemoryRequirements2

```
