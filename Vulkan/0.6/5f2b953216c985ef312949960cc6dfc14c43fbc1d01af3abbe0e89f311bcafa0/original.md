Extension: VK_KHR_swapchain

Arguments:

  * `wait_semaphores::Vector{Semaphore}`
  * `swapchains::Vector{SwapchainKHR}`
  * `image_indices::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `results::Vector{Result}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentInfoKHR.html)

```julia
_PresentInfoKHR(
    wait_semaphores::AbstractArray,
    swapchains::AbstractArray,
    image_indices::AbstractArray;
    next,
    results
) -> Vulkan._PresentInfoKHR

```
