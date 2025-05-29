VkPhysicalDeviceTransformFeedbackPropertiesEXTの高レベルラッパー。

拡張: VK*EXT*transform_feedback

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceTransformFeedbackPropertiesEXT.html)

```julia
struct PhysicalDeviceTransformFeedbackPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `max_transform_feedback_streams::UInt32`
  * `max_transform_feedback_buffers::UInt32`
  * `max_transform_feedback_buffer_size::UInt64`
  * `max_transform_feedback_stream_data_size::UInt32`
  * `max_transform_feedback_buffer_data_size::UInt32`
  * `max_transform_feedback_buffer_data_stride::UInt32`
  * `transform_feedback_queries::Bool`
  * `transform_feedback_streams_lines_triangles::Bool`
  * `transform_feedback_rasterization_stream_select::Bool`
  * `transform_feedback_draw::Bool`
