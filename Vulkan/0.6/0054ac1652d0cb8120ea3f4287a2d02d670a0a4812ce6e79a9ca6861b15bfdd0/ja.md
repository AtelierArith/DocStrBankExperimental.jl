拡張: VK*EXT*vertex*attribute*divisor

引数:

  * `vertex_binding_divisors::Vector{_VertexInputBindingDivisorDescriptionEXT}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineVertexInputDivisorStateCreateInfoEXT.html)

```julia
_PipelineVertexInputDivisorStateCreateInfoEXT(
    vertex_binding_divisors::AbstractArray;
    next
) -> Vulkan._PipelineVertexInputDivisorStateCreateInfoEXT

```
