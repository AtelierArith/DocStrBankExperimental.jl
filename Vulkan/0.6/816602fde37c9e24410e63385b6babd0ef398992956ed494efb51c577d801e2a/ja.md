VkBufferMemoryBarrierの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferMemoryBarrier.html)

```julia
struct BufferMemoryBarrier <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_access_mask::Vulkan.AccessFlag`
  * `dst_access_mask::Vulkan.AccessFlag`
  * `src_queue_family_index::UInt32`
  * `dst_queue_family_index::UInt32`
  * `buffer::Vulkan.Buffer`
  * `offset::UInt64`
  * `size::UInt64`
