拡張: VK*NV*present_barrier

引数:

  * `present_barrier_enable::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentBarrierCreateInfoNV.html)

```julia
SwapchainPresentBarrierCreateInfoNV(
    present_barrier_enable::Bool;
    next
) -> Vulkan.SwapchainPresentBarrierCreateInfoNV

```
