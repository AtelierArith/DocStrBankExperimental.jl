VkPipelineExecutablePropertiesKHRの高レベルラッパー。

拡張: VK*KHR*pipeline*executable*properties

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutablePropertiesKHR.html)

```julia
struct PipelineExecutablePropertiesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `stages::Vulkan.ShaderStageFlag`
  * `name::String`
  * `description::String`
  * `subgroup_size::UInt32`
