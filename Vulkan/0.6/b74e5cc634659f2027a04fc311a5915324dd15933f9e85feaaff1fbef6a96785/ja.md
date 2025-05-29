VkBufferCopyの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferCopy.html)

```julia
struct BufferCopy <: Vulkan.HighLevelStruct
```

  * `src_offset::UInt64`
  * `dst_offset::UInt64`
  * `size::UInt64`
