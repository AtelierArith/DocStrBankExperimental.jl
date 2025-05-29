Extension: VK_EXT_debug_utils

Arguments:

  * `instance::Instance`
  * `message_severity::DebugUtilsMessageSeverityFlagEXT`
  * `message_types::DebugUtilsMessageTypeFlagEXT`
  * `callback_data::DebugUtilsMessengerCallbackDataEXT`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSubmitDebugUtilsMessageEXT.html)

```julia
submit_debug_utils_message_ext(
    instance,
    message_severity::Vulkan.DebugUtilsMessageSeverityFlagEXT,
    message_types::Vulkan.DebugUtilsMessageTypeFlagEXT,
    callback_data::Vulkan.DebugUtilsMessengerCallbackDataEXT
)

```
