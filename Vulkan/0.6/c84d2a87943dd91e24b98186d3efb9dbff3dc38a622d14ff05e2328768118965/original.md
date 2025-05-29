Extension: VK_EXT_debug_utils

Arguments:

  * `message_id_number::Int32`
  * `message::String`
  * `queue_labels::Vector{_DebugUtilsLabelEXT}`
  * `cmd_buf_labels::Vector{_DebugUtilsLabelEXT}`
  * `objects::Vector{_DebugUtilsObjectNameInfoEXT}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `message_id_name::String`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsMessengerCallbackDataEXT.html)

```julia
_DebugUtilsMessengerCallbackDataEXT(
    message_id_number::Integer,
    message::AbstractString,
    queue_labels::AbstractArray,
    cmd_buf_labels::AbstractArray,
    objects::AbstractArray;
    next,
    flags,
    message_id_name
) -> Vulkan._DebugUtilsMessengerCallbackDataEXT

```
