Extension: VK_NV_present_barrier

Arguments:

  * `present_barrier_enable::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentBarrierCreateInfoNV.html)

```julia
SwapchainPresentBarrierCreateInfoNV(
    present_barrier_enable::Bool;
    next
) -> Vulkan.SwapchainPresentBarrierCreateInfoNV

```
