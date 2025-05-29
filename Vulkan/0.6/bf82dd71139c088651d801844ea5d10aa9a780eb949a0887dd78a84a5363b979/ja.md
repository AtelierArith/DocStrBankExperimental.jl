引数:

  * `stencil_usage::ImageUsageFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageStencilUsageCreateInfo.html)

```julia
_ImageStencilUsageCreateInfo(
    stencil_usage::Vulkan.ImageUsageFlag;
    next
) -> Vulkan._ImageStencilUsageCreateInfo

```
