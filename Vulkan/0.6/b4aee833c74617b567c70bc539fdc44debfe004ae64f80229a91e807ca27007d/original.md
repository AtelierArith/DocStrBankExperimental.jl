Extension: VK_EXT_debug_utils

Arguments:

  * `message_id_number::Int32`
  * `message::String`
  * `queue_labels::Vector{DebugUtilsLabelEXT}`
  * `cmd_buf_labels::Vector{DebugUtilsLabelEXT}`
  * `objects::Vector{DebugUtilsObjectNameInfoEXT}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `message_id_name::String`: defaults to ``

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsMessengerCallbackDataEXT.html)

```julia
DebugUtilsMessengerCallbackDataEXT(
    message_id_number::Integer,
    message::AbstractString,
    queue_labels::AbstractArray,
    cmd_buf_labels::AbstractArray,
    objects::AbstractArray;
    next,
    flags,
    message_id_name
) -> Vulkan.DebugUtilsMessengerCallbackDataEXT

```
