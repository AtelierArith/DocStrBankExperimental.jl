拡張: VK*EXT*vertex*input*dynamic_state

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `vertex_binding_descriptions::Vector{_VertexInputBindingDescription2EXT}`
  * `vertex_attribute_descriptions::Vector{_VertexInputAttributeDescription2EXT}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetVertexInputEXT.html)

```julia
_cmd_set_vertex_input_ext(
    command_buffer,
    vertex_binding_descriptions::AbstractArray,
    vertex_attribute_descriptions::AbstractArray
)

```
