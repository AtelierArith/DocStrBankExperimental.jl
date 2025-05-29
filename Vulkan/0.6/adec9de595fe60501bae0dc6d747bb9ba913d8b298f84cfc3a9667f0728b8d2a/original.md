Arguments:

  * `format::Format`
  * `type::ImageType`
  * `samples::SampleCountFlag`
  * `usage::ImageUsageFlag`
  * `tiling::ImageTiling`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSparseImageFormatInfo2.html)

```julia
_PhysicalDeviceSparseImageFormatInfo2(
    format::Vulkan.Format,
    type::Vulkan.ImageType,
    samples::Vulkan.SampleCountFlag,
    usage::Vulkan.ImageUsageFlag,
    tiling::Vulkan.ImageTiling;
    next
) -> Vulkan._PhysicalDeviceSparseImageFormatInfo2

```
