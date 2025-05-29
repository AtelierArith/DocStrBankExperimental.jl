拡張: VK*KHR*swapchain

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`
  * `ERROR_SURFACE_LOST_KHR`
  * `ERROR_NATIVE_WINDOW_IN_USE_KHR`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_COMPRESSION_EXHAUSTED_EXT`

引数:

  * `device::Device`
  * `surface::SurfaceKHR`
  * `min_image_count::UInt32`
  * `image_format::Format`
  * `image_color_space::ColorSpaceKHR`
  * `image_extent::Extent2D`
  * `image_array_layers::UInt32`
  * `image_usage::ImageUsageFlag`
  * `image_sharing_mode::SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `pre_transform::SurfaceTransformFlagKHR`
  * `composite_alpha::CompositeAlphaFlagKHR`
  * `present_mode::PresentModeKHR`
  * `clipped::Bool`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::SwapchainCreateFlagKHR`: デフォルトは `0`
  * `old_swapchain::SwapchainKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSwapchainKHR.html)

```julia
create_swapchain_khr(
    device,
    surface,
    min_image_count::Integer,
    image_format::Vulkan.Format,
    image_color_space::Vulkan.ColorSpaceKHR,
    image_extent::Vulkan.Extent2D,
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
) -> ResultTypes.Result{Vulkan.SwapchainKHR, Vulkan.VulkanError}

```
