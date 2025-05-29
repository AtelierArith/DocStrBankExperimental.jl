VkTraceRaysIndirectCommand2KHRの高レベルラッパー。

拡張: VK*KHR*ray*tracing*maintenance1

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkTraceRaysIndirectCommand2KHR.html)

```julia
struct TraceRaysIndirectCommand2KHR <: Vulkan.HighLevelStruct
```

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
