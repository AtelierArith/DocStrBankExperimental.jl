引数:

  * `usage::ImageUsageFlag`
  * `width::UInt32`
  * `height::UInt32`
  * `layer_count::UInt32`
  * `view_formats::Vector{Format}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::ImageCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferAttachmentImageInfo.html)

```julia
_FramebufferAttachmentImageInfo(
    usage::Vulkan.ImageUsageFlag,
    width::Integer,
    height::Integer,
    layer_count::Integer,
    view_formats::AbstractArray;
    next,
    flags
) -> Vulkan._FramebufferAttachmentImageInfo

```
