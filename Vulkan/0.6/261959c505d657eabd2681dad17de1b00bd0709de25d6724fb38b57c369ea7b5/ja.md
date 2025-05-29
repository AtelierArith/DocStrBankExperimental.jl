引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreCreateInfo.html)

```julia
_SemaphoreCreateInfo(
;
    next,
    flags
) -> Vulkan._SemaphoreCreateInfo

```
