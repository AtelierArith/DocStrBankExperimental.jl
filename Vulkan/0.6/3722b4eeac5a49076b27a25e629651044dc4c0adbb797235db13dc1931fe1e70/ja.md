引数:

  * `contents::SubpassContents`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassBeginInfo.html)

```julia
_SubpassBeginInfo(
    contents::Vulkan.SubpassContents;
    next
) -> Vulkan._SubpassBeginInfo

```
