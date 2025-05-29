拡張: VK*KHR*video_queue

引数:

  * `update_sequence_count::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionParametersUpdateInfoKHR.html)

```julia
_VideoSessionParametersUpdateInfoKHR(
    update_sequence_count::Integer;
    next
) -> Vulkan._VideoSessionParametersUpdateInfoKHR

```
