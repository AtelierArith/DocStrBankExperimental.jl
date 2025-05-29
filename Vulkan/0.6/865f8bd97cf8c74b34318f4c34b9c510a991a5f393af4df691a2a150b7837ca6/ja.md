拡張: VK*KHR*video_queue

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::VideoCodingControlFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoCodingControlInfoKHR.html)

```julia
_VideoCodingControlInfoKHR(
;
    next,
    flags
) -> Vulkan._VideoCodingControlInfoKHR

```
