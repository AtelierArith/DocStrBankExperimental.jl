High-level wrapper for VkSubpassDependency2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDependency2.html)

```julia
struct SubpassDependency2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_subpass::UInt32`
  * `dst_subpass::UInt32`
  * `src_stage_mask::Vulkan.PipelineStageFlag`
  * `dst_stage_mask::Vulkan.PipelineStageFlag`
  * `src_access_mask::Vulkan.AccessFlag`
  * `dst_access_mask::Vulkan.AccessFlag`
  * `dependency_flags::Vulkan.DependencyFlag`
  * `view_offset::Int32`
