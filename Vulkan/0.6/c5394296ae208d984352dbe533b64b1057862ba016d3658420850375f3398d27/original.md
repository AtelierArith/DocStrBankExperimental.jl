Extension: VK_KHR_video_queue

Arguments:

  * `profiles::Vector{_VideoProfileInfoKHR}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoProfileListInfoKHR.html)

```julia
_VideoProfileListInfoKHR(
    profiles::AbstractArray;
    next
) -> Vulkan._VideoProfileListInfoKHR

```
