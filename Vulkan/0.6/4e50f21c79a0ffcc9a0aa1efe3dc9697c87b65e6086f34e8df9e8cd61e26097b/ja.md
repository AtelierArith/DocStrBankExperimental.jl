VkPipelineCoverageModulationStateCreateInfoNVの高レベルラッパー。

拡張: VK*NV*framebuffer*mixed*samples

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCoverageModulationStateCreateInfoNV.html)

```julia
struct PipelineCoverageModulationStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `coverage_modulation_mode::Vulkan.CoverageModulationModeNV`
  * `coverage_modulation_table_enable::Bool`
  * `coverage_modulation_table::Union{Ptr{Nothing}, Vector{Float32}}`
