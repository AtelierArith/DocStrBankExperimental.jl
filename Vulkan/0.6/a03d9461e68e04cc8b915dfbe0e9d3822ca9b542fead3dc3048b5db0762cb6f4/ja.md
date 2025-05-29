拡張: VK*KHR*swapchain

引数:

  * `device::Device`
  * `surface::SurfaceKHR`
  * `min_image_count::UInt32`
  * `image_format::Format`
  * `image_color_space::ColorSpaceKHR`
  * `image_extent::_Extent2D`
  * `image_array_layers::UInt32`
  * `image_usage::ImageUsageFlag`
  * `image_sharing_mode::SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `pre_transform::SurfaceTransformFlagKHR`
  * `composite_alpha::CompositeAlphaFlagKHR`
  * `present_mode::PresentModeKHR`
  * `clipped::Bool`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::SwapchainCreateFlagKHR`: デフォルトは `0`
  * `old_swapchain::SwapchainKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSwapchainKHR.html)

```julia
SwapchainKHR(
    device,
    surface,
    min_image_count::Integer,
    image_format::Vulkan.Format,
    image_color_space::Vulkan.ColorSpaceKHR,
    image_extent::Vulkan._Extent2D,
    image_array_layers::Integer,
    image_usage::Vulkan.ImageUsageFlag,
    image_sharing_mode::Vulkan.SharingMode,
    queue_family_indices::AbstractArray,
    pre_transform::Vulkan.SurfaceTransformFlagKHR,
    composite_alpha::Vulkan.CompositeAlphaFlagKHR,
    present_mode::Vulkan.PresentModeKHR,
    clipped::Bool;
    allocator,
    next,
    flags,
    old_swapchain
) -> Vulkan.SwapchainKHR

```
