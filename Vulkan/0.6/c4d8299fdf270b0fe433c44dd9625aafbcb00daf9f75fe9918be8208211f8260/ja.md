VkMemoryAllocateFlagsInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryAllocateFlagsInfo.html)

```julia
struct MemoryAllocateFlagsInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.MemoryAllocateFlag`
  * `device_mask::UInt32`
