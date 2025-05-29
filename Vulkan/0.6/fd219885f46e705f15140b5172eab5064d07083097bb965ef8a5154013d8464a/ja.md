引数:

  * `physical_device::PhysicalDevice`
  * `format::Format`
  * `type::ImageType`
  * `samples::SampleCountFlag`
  * `usage::ImageUsageFlag`
  * `tiling::ImageTiling`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSparseImageFormatProperties.html)

```julia
_get_physical_device_sparse_image_format_properties(
    physical_device,
    format::Vulkan.Format,
    type::Vulkan.ImageType,
    samples::Vulkan.SampleCountFlag,
    usage::Vulkan.ImageUsageFlag,
    tiling::Vulkan.ImageTiling
) -> Vector{Vulkan._SparseImageFormatProperties}

```
