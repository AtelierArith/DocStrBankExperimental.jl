引数:

  * `rasterization_samples::SampleCountFlag`
  * `sample_shading_enable::Bool`
  * `min_sample_shading::Float32`
  * `alpha_to_coverage_enable::Bool`
  * `alpha_to_one_enable::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `sample_mask::Vector{UInt32}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineMultisampleStateCreateInfo.html)

```julia
_PipelineMultisampleStateCreateInfo(
    rasterization_samples::Vulkan.SampleCountFlag,
    sample_shading_enable::Bool,
    min_sample_shading::Real,
    alpha_to_coverage_enable::Bool,
    alpha_to_one_enable::Bool;
    next,
    flags,
    sample_mask
) -> Vulkan._PipelineMultisampleStateCreateInfo

```
