Extension: VK_KHR_video_queue

Arguments:

  * `profiles::Vector{VideoProfileInfoKHR}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoProfileListInfoKHR.html)

```julia
VideoProfileListInfoKHR(
    profiles::AbstractArray;
    next
) -> Vulkan.VideoProfileListInfoKHR

```
