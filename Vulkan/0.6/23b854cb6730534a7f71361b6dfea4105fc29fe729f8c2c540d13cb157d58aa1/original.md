Extension: VK_EXT_vertex_input_dynamic_state

Arguments:

  * `binding::UInt32`
  * `stride::UInt32`
  * `input_rate::VertexInputRate`
  * `divisor::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVertexInputBindingDescription2EXT.html)

```julia
VertexInputBindingDescription2EXT(
    binding::Integer,
    stride::Integer,
    input_rate::Vulkan.VertexInputRate,
    divisor::Integer;
    next
) -> Vulkan.VertexInputBindingDescription2EXT

```
