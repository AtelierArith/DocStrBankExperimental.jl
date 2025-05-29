高レベルのラッパー VkSwapchainCreateInfoKHR。

拡張: VK*KHR*swapchain

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainCreateInfoKHR.html)

```julia
struct SwapchainCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.SwapchainCreateFlagKHR`
  * `surface::Vulkan.SurfaceKHR`
  * `min_image_count::UInt32`
  * `image_format::Vulkan.Format`
  * `image_color_space::Vulkan.ColorSpaceKHR`
  * `image_extent::Vulkan.Extent2D`
  * `image_array_layers::UInt32`
  * `image_usage::Vulkan.ImageUsageFlag`
  * `image_sharing_mode::Vulkan.SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `pre_transform::Vulkan.SurfaceTransformFlagKHR`
  * `composite_alpha::Vulkan.CompositeAlphaFlagKHR`
  * `present_mode::Vulkan.PresentModeKHR`
  * `clipped::Bool`
  * `old_swapchain::Union{Ptr{Nothing}, Vulkan.SwapchainKHR}`
