VkAmigoProfilingSubmitInfoSECの高レベルラッパー。

拡張: VK*SEC*amigo_profiling

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAmigoProfilingSubmitInfoSEC.html)

```julia
struct AmigoProfilingSubmitInfoSEC <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `first_draw_timestamp::UInt64`
  * `swap_buffer_timestamp::UInt64`
