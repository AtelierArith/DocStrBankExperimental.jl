拡張: VK*NV*ray_tracing

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `raygen_shader_binding_table_buffer::Buffer`
  * `raygen_shader_binding_offset::UInt64`
  * `miss_shader_binding_offset::UInt64`
  * `miss_shader_binding_stride::UInt64`
  * `hit_shader_binding_offset::UInt64`
  * `hit_shader_binding_stride::UInt64`
  * `callable_shader_binding_offset::UInt64`
  * `callable_shader_binding_stride::UInt64`
  * `width::UInt32`
  * `height::UInt32`
  * `depth::UInt32`
  * `miss_shader_binding_table_buffer::Buffer`: デフォルトは `C_NULL`
  * `hit_shader_binding_table_buffer::Buffer`: デフォルトは `C_NULL`
  * `callable_shader_binding_table_buffer::Buffer`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdTraceRaysNV.html)

```julia
_cmd_trace_rays_nv(
    command_buffer,
    raygen_shader_binding_table_buffer,
    raygen_shader_binding_offset::Integer,
    miss_shader_binding_offset::Integer,
    miss_shader_binding_stride::Integer,
    hit_shader_binding_offset::Integer,
    hit_shader_binding_stride::Integer,
    callable_shader_binding_offset::Integer,
    callable_shader_binding_stride::Integer,
    width::Integer,
    height::Integer,
    depth::Integer;
    miss_shader_binding_table_buffer,
    hit_shader_binding_table_buffer,
    callable_shader_binding_table_buffer
)

```
