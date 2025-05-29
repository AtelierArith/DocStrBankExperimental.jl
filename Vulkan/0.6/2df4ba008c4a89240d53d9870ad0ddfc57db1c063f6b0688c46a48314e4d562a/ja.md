高レベルのラッパー VkPipelineRasterizationConservativeStateCreateInfoEXT。

拡張: VK*EXT*conservative_rasterization

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationConservativeStateCreateInfoEXT.html)

```julia
struct PipelineRasterizationConservativeStateCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `conservative_rasterization_mode::Vulkan.ConservativeRasterizationModeEXT`
  * `extra_primitive_overestimation_size::Float32`
