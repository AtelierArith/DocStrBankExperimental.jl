VkMemoryBarrierの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryBarrier.html)

```julia
struct MemoryBarrier <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_access_mask::Vulkan.AccessFlag`
  * `dst_access_mask::Vulkan.AccessFlag`
