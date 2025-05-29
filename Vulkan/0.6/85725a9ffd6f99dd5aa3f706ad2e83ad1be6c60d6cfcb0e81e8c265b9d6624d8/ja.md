拡張: VK*EXT*display_control

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `surface_counters::SurfaceCounterFlagEXT`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainCounterCreateInfoEXT.html)

```julia
_SwapchainCounterCreateInfoEXT(
;
    next,
    surface_counters
) -> Vulkan._SwapchainCounterCreateInfoEXT

```
