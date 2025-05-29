拡張: VK*KHR*video_queue

引数:

  * `video_session::VideoSessionKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `video_session_parameters_template::VideoSessionParametersKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionParametersCreateInfoKHR.html)

```julia
_VideoSessionParametersCreateInfoKHR(
    video_session;
    next,
    flags,
    video_session_parameters_template
) -> Vulkan._VideoSessionParametersCreateInfoKHR

```
