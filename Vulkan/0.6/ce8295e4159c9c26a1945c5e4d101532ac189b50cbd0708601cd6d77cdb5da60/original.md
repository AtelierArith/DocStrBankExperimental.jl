High-level wrapper for VkPipelineShaderStageCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineShaderStageCreateInfo.html)

```julia
struct PipelineShaderStageCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PipelineShaderStageCreateFlag`
  * `stage::Vulkan.ShaderStageFlag`
  * `_module::Union{Ptr{Nothing}, Vulkan.ShaderModule}`
  * `name::String`
  * `specialization_info::Union{Ptr{Nothing}, Vulkan.SpecializationInfo}`
