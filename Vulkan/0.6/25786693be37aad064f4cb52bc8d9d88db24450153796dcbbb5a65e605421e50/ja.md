VkBindSparseInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindSparseInfo.html)

```julia
struct BindSparseInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `wait_semaphores::Vector{Vulkan.Semaphore}`
  * `buffer_binds::Vector{Vulkan.SparseBufferMemoryBindInfo}`
  * `image_opaque_binds::Vector{Vulkan.SparseImageOpaqueMemoryBindInfo}`
  * `image_binds::Vector{Vulkan.SparseImageMemoryBindInfo}`
  * `signal_semaphores::Vector{Vulkan.Semaphore}`
