拡張: VK*EXT*swapchain_maintenance1

引数:

  * `fences::Vector{Fence}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentFenceInfoEXT.html)

```julia
_SwapchainPresentFenceInfoEXT(
    fences::AbstractArray;
    next
) -> Vulkan._SwapchainPresentFenceInfoEXT

```
