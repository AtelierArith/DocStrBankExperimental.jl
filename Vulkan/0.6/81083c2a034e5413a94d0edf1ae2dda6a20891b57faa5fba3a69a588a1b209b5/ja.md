拡張: VK*EXT*swapchain_maintenance1

引数:

  * `next::Any`: デフォルトは `C_NULL`
  * `scaling_behavior::PresentScalingFlagEXT`: デフォルトは `0`
  * `present_gravity_x::PresentGravityFlagEXT`: デフォルトは `0`
  * `present_gravity_y::PresentGravityFlagEXT`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentScalingCreateInfoEXT.html)

```julia
SwapchainPresentScalingCreateInfoEXT(
;
    next,
    scaling_behavior,
    present_gravity_x,
    present_gravity_y
) -> Vulkan.SwapchainPresentScalingCreateInfoEXT

```
