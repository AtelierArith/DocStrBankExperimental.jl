Extension: VK_NV_ray_tracing

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `acceleration_structures::Vector{AccelerationStructureNV}`
  * `query_type::QueryType`
  * `query_pool::QueryPool`
  * `first_query::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWriteAccelerationStructuresPropertiesNV.html)

```julia
cmd_write_acceleration_structures_properties_nv(
    command_buffer,
    acceleration_structures::AbstractArray,
    query_type::Vulkan.QueryType,
    query_pool,
    first_query::Integer
)

```
