Extension: VK_KHR_swapchain

Arguments:

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
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::SwapchainCreateFlagKHR`: defaults to `0`
  * `old_swapchain::SwapchainKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainCreateInfoKHR.html)

```julia
_SwapchainCreateInfoKHR(
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
    next,
    flags,
    old_swapchain
) -> Vulkan._SwapchainCreateInfoKHR

```
