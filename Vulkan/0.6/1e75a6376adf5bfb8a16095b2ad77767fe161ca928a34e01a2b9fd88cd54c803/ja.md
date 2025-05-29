VkSubpassDependencyの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDependency.html)

```julia
struct SubpassDependency <: Vulkan.HighLevelStruct
```

  * `src_subpass::UInt32`
  * `dst_subpass::UInt32`
  * `src_stage_mask::Vulkan.PipelineStageFlag`
  * `dst_stage_mask::Vulkan.PipelineStageFlag`
  * `src_access_mask::Vulkan.AccessFlag`
  * `dst_access_mask::Vulkan.AccessFlag`
  * `dependency_flags::Vulkan.DependencyFlag`
