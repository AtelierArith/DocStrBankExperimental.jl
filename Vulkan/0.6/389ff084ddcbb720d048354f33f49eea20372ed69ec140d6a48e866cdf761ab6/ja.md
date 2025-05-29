VkPipelineExecutableInternalRepresentationKHRの高レベルラッパー。

拡張: VK*KHR*pipeline*executable*properties

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableInternalRepresentationKHR.html)

```julia
struct PipelineExecutableInternalRepresentationKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `name::String`
  * `description::String`
  * `is_text::Bool`
  * `data_size::UInt64`
  * `data::Ptr{Nothing}`
