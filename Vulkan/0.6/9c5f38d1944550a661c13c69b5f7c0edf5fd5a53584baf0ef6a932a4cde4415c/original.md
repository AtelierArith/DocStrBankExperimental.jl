Extension: VK_EXT_vertex_input_dynamic_state

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `vertex_binding_descriptions::Vector{VertexInputBindingDescription2EXT}`
  * `vertex_attribute_descriptions::Vector{VertexInputAttributeDescription2EXT}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetVertexInputEXT.html)

```julia
cmd_set_vertex_input_ext(
    command_buffer,
    vertex_binding_descriptions::AbstractArray,
    vertex_attribute_descriptions::AbstractArray
)

```
