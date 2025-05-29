引数:

  * `usage::ImageUsageFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewUsageCreateInfo.html)

```julia
_ImageViewUsageCreateInfo(
    usage::Vulkan.ImageUsageFlag;
    next
) -> Vulkan._ImageViewUsageCreateInfo

```
