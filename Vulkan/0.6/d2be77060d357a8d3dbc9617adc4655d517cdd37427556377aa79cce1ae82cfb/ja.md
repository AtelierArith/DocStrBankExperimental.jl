VkBufferMemoryBarrier2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferMemoryBarrier2.html)

```julia
struct BufferMemoryBarrier2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_stage_mask::UInt64`
  * `src_access_mask::UInt64`
  * `dst_stage_mask::UInt64`
  * `dst_access_mask::UInt64`
  * `src_queue_family_index::UInt32`
  * `dst_queue_family_index::UInt32`
  * `buffer::Vulkan.Buffer`
  * `offset::UInt64`
  * `size::UInt64`
