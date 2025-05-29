引数:

  * `prefers_dedicated_allocation::Bool`
  * `requires_dedicated_allocation::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryDedicatedRequirements.html)

```julia
_MemoryDedicatedRequirements(
    prefers_dedicated_allocation::Bool,
    requires_dedicated_allocation::Bool;
    next
) -> Vulkan._MemoryDedicatedRequirements

```
