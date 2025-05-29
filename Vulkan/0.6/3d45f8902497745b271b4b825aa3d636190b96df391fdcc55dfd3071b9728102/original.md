Extension: VK_EXT_conservative_rasterization

Arguments:

  * `conservative_rasterization_mode::ConservativeRasterizationModeEXT`
  * `extra_primitive_overestimation_size::Float32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationConservativeStateCreateInfoEXT.html)

```julia
_PipelineRasterizationConservativeStateCreateInfoEXT(
    conservative_rasterization_mode::Vulkan.ConservativeRasterizationModeEXT,
    extra_primitive_overestimation_size::Real;
    next,
    flags
) -> Vulkan._PipelineRasterizationConservativeStateCreateInfoEXT

```
