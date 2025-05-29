Extension: VK_KHR_video_queue

Arguments:

  * `update_sequence_count::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionParametersUpdateInfoKHR.html)

```julia
_VideoSessionParametersUpdateInfoKHR(
    update_sequence_count::Integer;
    next
) -> Vulkan._VideoSessionParametersUpdateInfoKHR

```
