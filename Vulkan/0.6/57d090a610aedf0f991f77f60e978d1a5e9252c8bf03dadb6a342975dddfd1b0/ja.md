拡張: VK*NV*framebuffer*mixed*samples

引数:

  * `coverage_modulation_mode::CoverageModulationModeNV`
  * `coverage_modulation_table_enable::Bool`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `coverage_modulation_table::Vector{Float32}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCoverageModulationStateCreateInfoNV.html)

```julia
PipelineCoverageModulationStateCreateInfoNV(
    coverage_modulation_mode::Vulkan.CoverageModulationModeNV,
    coverage_modulation_table_enable::Bool;
    next,
    flags,
    coverage_modulation_table
) -> Vulkan.PipelineCoverageModulationStateCreateInfoNV

```
