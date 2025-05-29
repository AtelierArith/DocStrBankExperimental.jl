Extension: VK_EXT_debug_utils

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `instance::Instance`
  * `message_severity::DebugUtilsMessageSeverityFlagEXT`
  * `message_type::DebugUtilsMessageTypeFlagEXT`
  * `pfn_user_callback::FunctionPtr`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `user_data::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDebugUtilsMessengerEXT.html)

```julia
_create_debug_utils_messenger_ext(
    instance,
    message_severity::Vulkan.DebugUtilsMessageSeverityFlagEXT,
    message_type::Vulkan.DebugUtilsMessageTypeFlagEXT,
    pfn_user_callback::Union{Ptr{Nothing}, Base.CFunction};
    allocator,
    next,
    flags,
    user_data
) -> ResultTypes.Result{Vulkan.DebugUtilsMessengerEXT, Vulkan.VulkanError}

```
