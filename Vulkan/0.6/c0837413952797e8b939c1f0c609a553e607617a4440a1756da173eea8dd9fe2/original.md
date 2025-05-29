High-level wrapper for VkPipelineExecutableStatisticKHR.

Extension: VK_KHR_pipeline_executable_properties

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableStatisticKHR.html)

```julia
struct PipelineExecutableStatisticKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `name::String`
  * `description::String`
  * `format::Vulkan.PipelineExecutableStatisticFormatKHR`
  * `value::Vulkan.PipelineExecutableStatisticValueKHR`
