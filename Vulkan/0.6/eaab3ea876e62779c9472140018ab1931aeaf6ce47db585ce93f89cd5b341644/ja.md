VkImportMemoryFdInfoKHRの高レベルラッパー。

拡張: VK*KHR*external*memory*fd

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportMemoryFdInfoKHR.html)

```julia
struct ImportMemoryFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `handle_type::Vulkan.ExternalMemoryHandleTypeFlag`
  * `fd::Int64`
