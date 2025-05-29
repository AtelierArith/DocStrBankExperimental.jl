Extension: VK_EXT_transform_feedback

Arguments:

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
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceTransformFeedbackPropertiesEXT.html)

```julia
_PhysicalDeviceTransformFeedbackPropertiesEXT(
    max_transform_feedback_streams::Integer,
    max_transform_feedback_buffers::Integer,
    max_transform_feedback_buffer_size::Integer,
    max_transform_feedback_stream_data_size::Integer,
    max_transform_feedback_buffer_data_size::Integer,
    max_transform_feedback_buffer_data_stride::Integer,
    transform_feedback_queries::Bool,
    transform_feedback_streams_lines_triangles::Bool,
    transform_feedback_rasterization_stream_select::Bool,
    transform_feedback_draw::Bool;
    next
) -> Vulkan._PhysicalDeviceTransformFeedbackPropertiesEXT

```
