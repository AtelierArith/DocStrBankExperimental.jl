High-level wrapper for VkImportMemoryFdInfoKHR.

Extension: VK_KHR_external_memory_fd

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportMemoryFdInfoKHR.html)

```julia
struct ImportMemoryFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `handle_type::Vulkan.ExternalMemoryHandleTypeFlag`
  * `fd::Int64`
