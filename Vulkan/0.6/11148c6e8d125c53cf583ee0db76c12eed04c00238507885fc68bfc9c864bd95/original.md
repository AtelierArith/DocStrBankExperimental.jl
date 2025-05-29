Arguments:

  * `set_layouts::Vector{DescriptorSetLayout}`
  * `push_constant_ranges::Vector{_PushConstantRange}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::PipelineLayoutCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineLayoutCreateInfo.html)

```julia
_PipelineLayoutCreateInfo(
    set_layouts::AbstractArray,
    push_constant_ranges::AbstractArray;
    next,
    flags
) -> Vulkan._PipelineLayoutCreateInfo

```
