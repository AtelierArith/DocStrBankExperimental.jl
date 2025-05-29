Extension: VK_EXT_swapchain_maintenance1

Arguments:

  * `next::Any`: defaults to `C_NULL`
  * `scaling_behavior::PresentScalingFlagEXT`: defaults to `0`
  * `present_gravity_x::PresentGravityFlagEXT`: defaults to `0`
  * `present_gravity_y::PresentGravityFlagEXT`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentScalingCreateInfoEXT.html)

```julia
SwapchainPresentScalingCreateInfoEXT(
;
    next,
    scaling_behavior,
    present_gravity_x,
    present_gravity_y
) -> Vulkan.SwapchainPresentScalingCreateInfoEXT

```
