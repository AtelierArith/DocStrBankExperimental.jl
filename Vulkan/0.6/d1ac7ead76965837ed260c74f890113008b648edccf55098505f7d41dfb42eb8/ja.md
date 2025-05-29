引数:

  * `next::Any`: デフォルトは `C_NULL`
  * `flags::CommandBufferUsageFlag`: デフォルトは `0`
  * `inheritance_info::CommandBufferInheritanceInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferBeginInfo.html)

```julia
CommandBufferBeginInfo(
;
    next,
    flags,
    inheritance_info
) -> Vulkan.CommandBufferBeginInfo

```
