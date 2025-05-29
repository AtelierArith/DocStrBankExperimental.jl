High-level wrapper for VkFramebufferMixedSamplesCombinationNV.

Extension: VK_NV_coverage_reduction_mode

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferMixedSamplesCombinationNV.html)

```julia
struct FramebufferMixedSamplesCombinationNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `coverage_reduction_mode::Vulkan.CoverageReductionModeNV`
  * `rasterization_samples::Vulkan.SampleCountFlag`
  * `depth_stencil_samples::Vulkan.SampleCountFlag`
  * `color_samples::Vulkan.SampleCountFlag`
