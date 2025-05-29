VkVideoSessionParametersCreateInfoKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionParametersCreateInfoKHR.html)

```julia
struct VideoSessionParametersCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `video_session_parameters_template::Union{Ptr{Nothing}, Vulkan.VideoSessionParametersKHR}`
  * `video_session::Vulkan.VideoSessionKHR`
