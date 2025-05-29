拡張: VK*KHR*video_queue

引数:

  * `profiles::Vector{_VideoProfileInfoKHR}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoProfileListInfoKHR.html)

```julia
_VideoProfileListInfoKHR(
    profiles::AbstractArray;
    next
) -> Vulkan._VideoProfileListInfoKHR

```
