VkBufferCopy2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferCopy2.html)

```julia
struct BufferCopy2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_offset::UInt64`
  * `dst_offset::UInt64`
  * `size::UInt64`
