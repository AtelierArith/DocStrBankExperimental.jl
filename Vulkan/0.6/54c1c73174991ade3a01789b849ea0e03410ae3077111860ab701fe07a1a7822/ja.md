拡張: VK*EXT*debug_utils

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `instance::Instance`
  * `message_severity::DebugUtilsMessageSeverityFlagEXT`
  * `message_type::DebugUtilsMessageTypeFlagEXT`
  * `pfn_user_callback::FunctionPtr`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `user_data::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDebugUtilsMessengerEXT.html)

```julia
create_debug_utils_messenger_ext(
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
