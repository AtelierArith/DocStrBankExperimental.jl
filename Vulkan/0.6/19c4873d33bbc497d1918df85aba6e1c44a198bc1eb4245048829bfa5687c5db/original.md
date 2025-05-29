Extension: VK_EXT_opacity_micromap

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `micromaps::Vector{MicromapEXT}`
  * `query_type::QueryType`
  * `query_pool::QueryPool`
  * `first_query::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWriteMicromapsPropertiesEXT.html)

```julia
cmd_write_micromaps_properties_ext(
    command_buffer,
    micromaps::AbstractArray,
    query_type::Vulkan.QueryType,
    query_pool,
    first_query::Integer
)

```
