拡張: VK*NV*coverage*reduction*mode

引数:

  * `coverage_reduction_mode::CoverageReductionModeNV`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCoverageReductionStateCreateInfoNV.html)

```julia
_PipelineCoverageReductionStateCreateInfoNV(
    coverage_reduction_mode::Vulkan.CoverageReductionModeNV;
    next,
    flags
) -> Vulkan._PipelineCoverageReductionStateCreateInfoNV

```
