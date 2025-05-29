拡張: VK*NV*coverage*reduction*mode

引数:

  * `coverage_reduction_mode::CoverageReductionModeNV`
  * `rasterization_samples::SampleCountFlag`
  * `depth_stencil_samples::SampleCountFlag`
  * `color_samples::SampleCountFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferMixedSamplesCombinationNV.html)

```julia
_FramebufferMixedSamplesCombinationNV(
    coverage_reduction_mode::Vulkan.CoverageReductionModeNV,
    rasterization_samples::Vulkan.SampleCountFlag,
    depth_stencil_samples::Vulkan.SampleCountFlag,
    color_samples::Vulkan.SampleCountFlag;
    next
) -> Vulkan._FramebufferMixedSamplesCombinationNV

```
