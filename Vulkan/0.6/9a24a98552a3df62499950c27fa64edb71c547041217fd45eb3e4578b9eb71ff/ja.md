VkRayTracingPipelineCreateInfoKHRの高レベルラッパー。

拡張: VK*KHR*ray*tracing*pipeline

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingPipelineCreateInfoKHR.html)

```julia
struct RayTracingPipelineCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PipelineCreateFlag`
  * `stages::Vector{Vulkan.PipelineShaderStageCreateInfo}`
  * `groups::Vector{Vulkan.RayTracingShaderGroupCreateInfoKHR}`
  * `max_pipeline_ray_recursion_depth::UInt32`
  * `library_info::Union{Ptr{Nothing}, Vulkan.PipelineLibraryCreateInfoKHR}`
  * `library_interface::Union{Ptr{Nothing}, Vulkan.RayTracingPipelineInterfaceCreateInfoKHR}`
  * `dynamic_state::Union{Ptr{Nothing}, Vulkan.PipelineDynamicStateCreateInfo}`
  * `layout::Vulkan.PipelineLayout`
  * `base_pipeline_handle::Union{Ptr{Nothing}, Vulkan.Pipeline}`
  * `base_pipeline_index::Int32`
