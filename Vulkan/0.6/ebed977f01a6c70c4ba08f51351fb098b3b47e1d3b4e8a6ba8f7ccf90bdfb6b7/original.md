High-level wrapper for VkPipelineInputAssemblyStateCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineInputAssemblyStateCreateInfo.html)

```julia
struct PipelineInputAssemblyStateCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `topology::Vulkan.PrimitiveTopology`
  * `primitive_restart_enable::Bool`
