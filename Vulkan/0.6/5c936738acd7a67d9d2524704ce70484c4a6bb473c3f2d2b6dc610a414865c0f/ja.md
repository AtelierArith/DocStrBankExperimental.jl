引数:

  * `view_formats::Vector{Format}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageFormatListCreateInfo.html)

```julia
ImageFormatListCreateInfo(
    view_formats::AbstractArray;
    next
) -> Vulkan.ImageFormatListCreateInfo

```
