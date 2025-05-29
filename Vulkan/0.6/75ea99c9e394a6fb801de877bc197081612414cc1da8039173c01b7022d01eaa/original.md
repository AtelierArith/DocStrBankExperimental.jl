Extension: VK_KHR_ray_tracing_maintenance1

Arguments:

  * `raygen_shader_record_address::UInt64`
  * `raygen_shader_record_size::UInt64`
  * `miss_shader_binding_table_address::UInt64`
  * `miss_shader_binding_table_size::UInt64`
  * `miss_shader_binding_table_stride::UInt64`
  * `hit_shader_binding_table_address::UInt64`
  * `hit_shader_binding_table_size::UInt64`
  * `hit_shader_binding_table_stride::UInt64`
  * `callable_shader_binding_table_address::UInt64`
  * `callable_shader_binding_table_size::UInt64`
  * `callable_shader_binding_table_stride::UInt64`
  * `width::UInt32`
  * `height::UInt32`
  * `depth::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkTraceRaysIndirectCommand2KHR.html)

```julia
_TraceRaysIndirectCommand2KHR(
    raygen_shader_record_address::Integer,
    raygen_shader_record_size::Integer,
    miss_shader_binding_table_address::Integer,
    miss_shader_binding_table_size::Integer,
    miss_shader_binding_table_stride::Integer,
    hit_shader_binding_table_address::Integer,
    hit_shader_binding_table_size::Integer,
    hit_shader_binding_table_stride::Integer,
    callable_shader_binding_table_address::Integer,
    callable_shader_binding_table_size::Integer,
    callable_shader_binding_table_stride::Integer,
    width::Integer,
    height::Integer,
    depth::Integer
) -> Vulkan._TraceRaysIndirectCommand2KHR

```
