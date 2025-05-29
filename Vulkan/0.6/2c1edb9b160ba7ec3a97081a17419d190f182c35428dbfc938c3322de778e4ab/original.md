Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_COMPRESSION_EXHAUSTED_EXT`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

Arguments:

  * `device::Device`
  * `image_type::ImageType`
  * `format::Format`
  * `extent::_Extent3D`
  * `mip_levels::UInt32`
  * `array_layers::UInt32`
  * `samples::SampleCountFlag`
  * `tiling::ImageTiling`
  * `usage::ImageUsageFlag`
  * `sharing_mode::SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `initial_layout::ImageLayout`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::ImageCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateImage.html)

```julia
_create_image(
    device,
    image_type::Vulkan.ImageType,
    format::Vulkan.Format,
    extent::Vulkan._Extent3D,
    mip_levels::Integer,
    array_layers::Integer,
    samples::Vulkan.SampleCountFlag,
    tiling::Vulkan.ImageTiling,
    usage::Vulkan.ImageUsageFlag,
    sharing_mode::Vulkan.SharingMode,
    queue_family_indices::AbstractArray,
    initial_layout::Vulkan.ImageLayout;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.Image, Vulkan.VulkanError}

```
