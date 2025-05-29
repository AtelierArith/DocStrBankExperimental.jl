High-level wrapper for VkSwapchainPresentScalingCreateInfoEXT.

Extension: VK_EXT_swapchain_maintenance1

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentScalingCreateInfoEXT.html)

```julia
struct SwapchainPresentScalingCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `scaling_behavior::Vulkan.PresentScalingFlagEXT`
  * `present_gravity_x::Vulkan.PresentGravityFlagEXT`
  * `present_gravity_y::Vulkan.PresentGravityFlagEXT`
