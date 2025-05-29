VK*GOOGLE*display_timingのVkPastPresentationTimingGOOGLEの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPastPresentationTimingGOOGLE.html)

```julia
struct PastPresentationTimingGOOGLE <: Vulkan.HighLevelStruct
```

  * `present_id::UInt32`
  * `desired_present_time::UInt64`
  * `actual_present_time::UInt64`
  * `earliest_present_time::UInt64`
  * `present_margin::UInt64`
