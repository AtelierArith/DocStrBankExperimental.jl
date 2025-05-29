高レベルラッパー VkMemoryGetFdInfoKHR。

拡張: VK*KHR*external*memory*fd

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetFdInfoKHR.html)

```julia
struct MemoryGetFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `memory::Vulkan.DeviceMemory`
  * `handle_type::Vulkan.ExternalMemoryHandleTypeFlag`
