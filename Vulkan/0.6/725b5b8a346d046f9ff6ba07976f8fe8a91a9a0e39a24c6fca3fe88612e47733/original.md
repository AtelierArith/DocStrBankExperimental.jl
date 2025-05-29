Extension: VK_EXT_debug_utils

Arguments:

  * `instance::Instance`
  * `message_severity::DebugUtilsMessageSeverityFlagEXT`
  * `message_type::DebugUtilsMessageTypeFlagEXT`
  * `pfn_user_callback::FunctionPtr`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `user_data::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDebugUtilsMessengerEXT.html)

```julia
DebugUtilsMessengerEXT(
    instance,
    message_severity::Vulkan.DebugUtilsMessageSeverityFlagEXT,
    message_type::Vulkan.DebugUtilsMessageTypeFlagEXT,
    pfn_user_callback::Union{Ptr{Nothing}, Base.CFunction};
    allocator,
    next,
    flags,
    user_data
) -> Vulkan.DebugUtilsMessengerEXT

```
