Arguments:

  * `usage::ImageUsageFlag`
  * `width::UInt32`
  * `height::UInt32`
  * `layer_count::UInt32`
  * `view_formats::Vector{Format}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::ImageCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferAttachmentImageInfo.html)

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
