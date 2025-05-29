Extension: VK_NV_coverage_reduction_mode

Arguments:

  * `coverage_reduction_mode::CoverageReductionModeNV`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCoverageReductionStateCreateInfoNV.html)

```julia
_PipelineCoverageReductionStateCreateInfoNV(
    coverage_reduction_mode::Vulkan.CoverageReductionModeNV;
    next,
    flags
) -> Vulkan._PipelineCoverageReductionStateCreateInfoNV

```
