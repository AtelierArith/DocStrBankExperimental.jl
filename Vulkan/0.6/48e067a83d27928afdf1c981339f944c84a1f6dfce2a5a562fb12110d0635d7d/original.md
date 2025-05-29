Extension: VK_EXT_vertex_attribute_divisor

Arguments:

  * `vertex_binding_divisors::Vector{VertexInputBindingDivisorDescriptionEXT}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineVertexInputDivisorStateCreateInfoEXT.html)

```julia
PipelineVertexInputDivisorStateCreateInfoEXT(
    vertex_binding_divisors::AbstractArray;
    next
) -> Vulkan.PipelineVertexInputDivisorStateCreateInfoEXT

```
