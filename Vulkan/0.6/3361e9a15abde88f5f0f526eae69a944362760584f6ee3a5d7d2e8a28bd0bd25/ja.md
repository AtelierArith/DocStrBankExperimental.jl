VkCopyBufferInfo2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyBufferInfo2.html)

```julia
struct CopyBufferInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_buffer::Vulkan.Buffer`
  * `dst_buffer::Vulkan.Buffer`
  * `regions::Vector{Vulkan.BufferCopy2}`
