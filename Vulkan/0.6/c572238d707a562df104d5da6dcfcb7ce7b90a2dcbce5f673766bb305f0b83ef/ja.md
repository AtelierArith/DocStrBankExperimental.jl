VkSparseImageMemoryBindInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryBindInfo.html)

```julia
struct SparseImageMemoryBindInfo <: Vulkan.HighLevelStruct
```

  * `image::Vulkan.Image`
  * `binds::Vector{Vulkan.SparseImageMemoryBind}`
