High-level wrapper for VkImportMemoryHostPointerInfoEXT.

Extension: VK_EXT_external_memory_host

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportMemoryHostPointerInfoEXT.html)

```julia
struct ImportMemoryHostPointerInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `handle_type::Vulkan.ExternalMemoryHandleTypeFlag`
  * `host_pointer::Ptr{Nothing}`
