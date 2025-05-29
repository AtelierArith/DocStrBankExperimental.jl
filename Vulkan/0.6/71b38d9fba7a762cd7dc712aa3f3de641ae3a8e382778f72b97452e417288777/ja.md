拡張: VK*KHR*video_queue

引数:

  * `profiles::Vector{VideoProfileInfoKHR}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoProfileListInfoKHR.html)

```julia
VideoProfileListInfoKHR(
    profiles::AbstractArray;
    next
) -> Vulkan.VideoProfileListInfoKHR

```
