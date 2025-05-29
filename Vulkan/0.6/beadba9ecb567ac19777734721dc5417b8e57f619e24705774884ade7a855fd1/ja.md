引数:

  * `format::Format`
  * `type::ImageType`
  * `tiling::ImageTiling`
  * `usage::ImageUsageFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::ImageCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageFormatInfo2.html)

```julia
_PhysicalDeviceImageFormatInfo2(
    format::Vulkan.Format,
    type::Vulkan.ImageType,
    tiling::Vulkan.ImageTiling,
    usage::Vulkan.ImageUsageFlag;
    next,
    flags
) -> Vulkan._PhysicalDeviceImageFormatInfo2

```
