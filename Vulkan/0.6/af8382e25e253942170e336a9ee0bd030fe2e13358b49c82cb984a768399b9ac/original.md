Arguments:

  * `rasterization_samples::SampleCountFlag`
  * `sample_shading_enable::Bool`
  * `min_sample_shading::Float32`
  * `alpha_to_coverage_enable::Bool`
  * `alpha_to_one_enable::Bool`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `sample_mask::Vector{UInt32}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineMultisampleStateCreateInfo.html)

```julia
PipelineMultisampleStateCreateInfo(
    rasterization_samples::Vulkan.SampleCountFlag,
    sample_shading_enable::Bool,
    min_sample_shading::Real,
    alpha_to_coverage_enable::Bool,
    alpha_to_one_enable::Bool;
    next,
    flags,
    sample_mask
) -> Vulkan.PipelineMultisampleStateCreateInfo

```
