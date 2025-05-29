Extension: VK_EXT_display_control

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `surface_counters::SurfaceCounterFlagEXT`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainCounterCreateInfoEXT.html)

```julia
_SwapchainCounterCreateInfoEXT(
;
    next,
    surface_counters
) -> Vulkan._SwapchainCounterCreateInfoEXT

```
