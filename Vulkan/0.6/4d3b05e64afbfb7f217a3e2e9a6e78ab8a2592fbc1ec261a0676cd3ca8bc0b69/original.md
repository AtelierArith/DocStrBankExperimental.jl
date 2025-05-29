Extension: VK_KHR_acceleration_structure

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `acceleration_structures::Vector{AccelerationStructureKHR}`
  * `query_type::QueryType`
  * `query_pool::QueryPool`
  * `first_query::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWriteAccelerationStructuresPropertiesKHR.html)

```julia
_cmd_write_acceleration_structures_properties_khr(
    command_buffer,
    acceleration_structures::AbstractArray,
    query_type::Vulkan.QueryType,
    query_pool,
    first_query::Integer
)

```
