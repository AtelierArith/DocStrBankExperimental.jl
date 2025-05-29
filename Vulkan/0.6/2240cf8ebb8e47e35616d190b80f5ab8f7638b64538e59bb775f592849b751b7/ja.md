引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::CommandBufferUsageFlag`: デフォルトは `0`
  * `inheritance_info::_CommandBufferInheritanceInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferBeginInfo.html)

```julia
_CommandBufferBeginInfo(
;
    next,
    flags,
    inheritance_info
) -> Vulkan._CommandBufferBeginInfo

```
