引数:

  * `set_layouts::Vector{DescriptorSetLayout}`
  * `push_constant_ranges::Vector{PushConstantRange}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::PipelineLayoutCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineLayoutCreateInfo.html)

```julia
PipelineLayoutCreateInfo(
    set_layouts::AbstractArray,
    push_constant_ranges::AbstractArray;
    next,
    flags
) -> Vulkan.PipelineLayoutCreateInfo

```
