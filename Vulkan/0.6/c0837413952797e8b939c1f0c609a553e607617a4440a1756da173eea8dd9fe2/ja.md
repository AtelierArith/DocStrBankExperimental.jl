VkPipelineExecutableStatisticKHRの高レベルラッパー。

拡張: VK*KHR*pipeline*executable*properties

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableStatisticKHR.html)

```julia
struct PipelineExecutableStatisticKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `name::String`
  * `description::String`
  * `format::Vulkan.PipelineExecutableStatisticFormatKHR`
  * `value::Vulkan.PipelineExecutableStatisticValueKHR`
