Extension: VK_EXT_debug_report

Arguments:

  * `instance::Instance`
  * `flags::DebugReportFlagEXT`
  * `object_type::DebugReportObjectTypeEXT`
  * `object::UInt64`
  * `location::UInt`
  * `message_code::Int32`
  * `layer_prefix::String`
  * `message::String`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDebugReportMessageEXT.html)

```julia
_debug_report_message_ext(
    instance,
    flags::Vulkan.DebugReportFlagEXT,
    object_type::Vulkan.DebugReportObjectTypeEXT,
    object::Integer,
    location::Integer,
    message_code::Integer,
    layer_prefix::AbstractString,
    message::AbstractString
)

```
