拡張: VK*EXT*debug_utils

引数:

  * `message_id_number::Int32`
  * `message::String`
  * `queue_labels::Vector{_DebugUtilsLabelEXT}`
  * `cmd_buf_labels::Vector{_DebugUtilsLabelEXT}`
  * `objects::Vector{_DebugUtilsObjectNameInfoEXT}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `message_id_name::String`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsMessengerCallbackDataEXT.html)

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
