Arguments:

  * `vertex_binding_descriptions::Vector{_VertexInputBindingDescription}`
  * `vertex_attribute_descriptions::Vector{_VertexInputAttributeDescription}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineVertexInputStateCreateInfo.html)

```julia
_PipelineVertexInputStateCreateInfo(
    vertex_binding_descriptions::AbstractArray,
    vertex_attribute_descriptions::AbstractArray;
    next,
    flags
) -> Vulkan._PipelineVertexInputStateCreateInfo

```
