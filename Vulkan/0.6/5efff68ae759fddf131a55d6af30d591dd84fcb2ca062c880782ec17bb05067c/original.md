High-level wrapper for VkDescriptorSetLayoutBinding.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutBinding.html)

```julia
struct DescriptorSetLayoutBinding <: Vulkan.HighLevelStruct
```

  * `binding::UInt32`
  * `descriptor_type::Vulkan.DescriptorType`
  * `descriptor_count::UInt32`
  * `stage_flags::Vulkan.ShaderStageFlag`
  * `immutable_samplers::Union{Ptr{Nothing}, Vector{Vulkan.Sampler}}`
