High-level wrapper for VkPipelineExecutableInfoKHR.

Extension: VK_KHR_pipeline_executable_properties

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineExecutableInfoKHR.html)

```julia
struct PipelineExecutableInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `pipeline::Vulkan.Pipeline`
  * `executable_index::UInt32`
