拡張: VK*EXT*opacity_micromap

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `micromaps::Vector{MicromapEXT}`
  * `query_type::QueryType`
  * `query_pool::QueryPool`
  * `first_query::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWriteMicromapsPropertiesEXT.html)

```julia
cmd_write_micromaps_properties_ext(
    command_buffer,
    micromaps::AbstractArray,
    query_type::Vulkan.QueryType,
    query_pool,
    first_query::Integer
)

```
