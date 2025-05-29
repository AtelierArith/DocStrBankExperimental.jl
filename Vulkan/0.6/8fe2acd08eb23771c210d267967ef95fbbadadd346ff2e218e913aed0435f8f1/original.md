High-level wrapper for VkPushConstantRange.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPushConstantRange.html)

```julia
struct PushConstantRange <: Vulkan.HighLevelStruct
```

  * `stage_flags::Vulkan.ShaderStageFlag`
  * `offset::UInt32`
  * `size::UInt32`
