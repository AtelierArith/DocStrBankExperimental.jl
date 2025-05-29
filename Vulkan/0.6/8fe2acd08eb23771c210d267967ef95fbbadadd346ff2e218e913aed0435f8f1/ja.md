VkPushConstantRangeの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPushConstantRange.html)

```julia
struct PushConstantRange <: Vulkan.HighLevelStruct
```

  * `stage_flags::Vulkan.ShaderStageFlag`
  * `offset::UInt32`
  * `size::UInt32`
