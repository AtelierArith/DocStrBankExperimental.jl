Extension: VK_EXT_vertex_input_dynamic_state

Arguments:

  * `location::UInt32`
  * `binding::UInt32`
  * `format::Format`
  * `offset::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVertexInputAttributeDescription2EXT.html)

```julia
_VertexInputAttributeDescription2EXT(
    location::Integer,
    binding::Integer,
    format::Vulkan.Format,
    offset::Integer;
    next
) -> Vulkan._VertexInputAttributeDescription2EXT

```
