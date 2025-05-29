VkDebugUtilsMessengerCallbackDataEXTの高レベルラッパー。

拡張: VK*EXT*debug_utils

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDebugUtilsMessengerCallbackDataEXT.html)

```julia
struct DebugUtilsMessengerCallbackDataEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `message_id_name::String`
  * `message_id_number::Int32`
  * `message::String`
  * `queue_labels::Vector{Vulkan.DebugUtilsLabelEXT}`
  * `cmd_buf_labels::Vector{Vulkan.DebugUtilsLabelEXT}`
  * `objects::Vector{Vulkan.DebugUtilsObjectNameInfoEXT}`
