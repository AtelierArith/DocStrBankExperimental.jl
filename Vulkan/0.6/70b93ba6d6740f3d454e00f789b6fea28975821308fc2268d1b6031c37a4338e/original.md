Arguments:

  * `usage::ImageUsageFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewUsageCreateInfo.html)

```julia
_ImageViewUsageCreateInfo(
    usage::Vulkan.ImageUsageFlag;
    next
) -> Vulkan._ImageViewUsageCreateInfo

```
