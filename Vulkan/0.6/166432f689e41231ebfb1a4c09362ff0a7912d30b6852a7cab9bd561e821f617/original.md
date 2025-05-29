Extension: VK_NV_coverage_reduction_mode

Arguments:

  * `coverage_reduction_mode::CoverageReductionModeNV`
  * `rasterization_samples::SampleCountFlag`
  * `depth_stencil_samples::SampleCountFlag`
  * `color_samples::SampleCountFlag`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferMixedSamplesCombinationNV.html)

```julia
FramebufferMixedSamplesCombinationNV(
    coverage_reduction_mode::Vulkan.CoverageReductionModeNV,
    rasterization_samples::Vulkan.SampleCountFlag,
    depth_stencil_samples::Vulkan.SampleCountFlag,
    color_samples::Vulkan.SampleCountFlag;
    next
) -> Vulkan.FramebufferMixedSamplesCombinationNV

```
