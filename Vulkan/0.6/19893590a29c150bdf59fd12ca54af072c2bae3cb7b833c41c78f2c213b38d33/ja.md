VkFramebufferMixedSamplesCombinationNVの高レベルラッパー。

拡張: VK*NV*coverage*reduction*mode

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferMixedSamplesCombinationNV.html)

```julia
struct FramebufferMixedSamplesCombinationNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `coverage_reduction_mode::Vulkan.CoverageReductionModeNV`
  * `rasterization_samples::Vulkan.SampleCountFlag`
  * `depth_stencil_samples::Vulkan.SampleCountFlag`
  * `color_samples::Vulkan.SampleCountFlag`
