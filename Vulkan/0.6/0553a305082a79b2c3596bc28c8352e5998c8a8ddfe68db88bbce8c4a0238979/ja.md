拡張: VK*NV*present_barrier

引数:

  * `present_barrier_enable::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentBarrierCreateInfoNV.html)

```julia
_SwapchainPresentBarrierCreateInfoNV(
    present_barrier_enable::Bool;
    next
) -> Vulkan._SwapchainPresentBarrierCreateInfoNV

```
