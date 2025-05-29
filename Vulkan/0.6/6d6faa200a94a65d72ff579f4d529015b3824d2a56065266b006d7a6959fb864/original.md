Arguments:

  * `vertex_binding_descriptions::Vector{VertexInputBindingDescription}`
  * `vertex_attribute_descriptions::Vector{VertexInputAttributeDescription}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineVertexInputStateCreateInfo.html)

```julia
PipelineVertexInputStateCreateInfo(
    vertex_binding_descriptions::AbstractArray,
    vertex_attribute_descriptions::AbstractArray;
    next,
    flags
) -> Vulkan.PipelineVertexInputStateCreateInfo

```
