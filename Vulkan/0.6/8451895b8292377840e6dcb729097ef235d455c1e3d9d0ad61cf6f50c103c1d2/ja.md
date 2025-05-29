拡張: VK*KHR*swapchain

引数:

  * `wait_semaphores::Vector{Semaphore}`
  * `swapchains::Vector{SwapchainKHR}`
  * `image_indices::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`
  * `results::Vector{Result}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentInfoKHR.html)

```julia
PresentInfoKHR(
    wait_semaphores::AbstractArray,
    swapchains::AbstractArray,
    image_indices::AbstractArray;
    next,
    results
) -> Vulkan.PresentInfoKHR

```
