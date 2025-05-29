Extension: VK_NV_framebuffer_mixed_samples

Arguments:

  * `coverage_modulation_mode::CoverageModulationModeNV`
  * `coverage_modulation_table_enable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `coverage_modulation_table::Vector{Float32}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCoverageModulationStateCreateInfoNV.html)

```julia
_PipelineCoverageModulationStateCreateInfoNV(
    coverage_modulation_mode::Vulkan.CoverageModulationModeNV,
    coverage_modulation_table_enable::Bool;
    next,
    flags,
    coverage_modulation_table
) -> Vulkan._PipelineCoverageModulationStateCreateInfoNV

```
