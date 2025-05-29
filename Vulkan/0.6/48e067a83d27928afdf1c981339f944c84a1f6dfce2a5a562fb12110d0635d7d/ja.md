拡張: VK*EXT*vertex*attribute*divisor

引数:

  * `vertex_binding_divisors::Vector{VertexInputBindingDivisorDescriptionEXT}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineVertexInputDivisorStateCreateInfoEXT.html)

```julia
PipelineVertexInputDivisorStateCreateInfoEXT(
    vertex_binding_divisors::AbstractArray;
    next
) -> Vulkan.PipelineVertexInputDivisorStateCreateInfoEXT

```
