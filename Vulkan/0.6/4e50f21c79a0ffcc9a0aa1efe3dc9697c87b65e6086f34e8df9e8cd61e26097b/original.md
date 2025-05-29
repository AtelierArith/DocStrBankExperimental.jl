High-level wrapper for VkPipelineCoverageModulationStateCreateInfoNV.

Extension: VK_NV_framebuffer_mixed_samples

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCoverageModulationStateCreateInfoNV.html)

```julia
struct PipelineCoverageModulationStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `coverage_modulation_mode::Vulkan.CoverageModulationModeNV`
  * `coverage_modulation_table_enable::Bool`
  * `coverage_modulation_table::Union{Ptr{Nothing}, Vector{Float32}}`
