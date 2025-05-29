VkImportMemoryHostPointerInfoEXTの高レベルラッパー。

拡張: VK*EXT*external*memory*host

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportMemoryHostPointerInfoEXT.html)

```julia
struct ImportMemoryHostPointerInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `handle_type::Vulkan.ExternalMemoryHandleTypeFlag`
  * `host_pointer::Ptr{Nothing}`
