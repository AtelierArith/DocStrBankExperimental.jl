VkDedicatedAllocationMemoryAllocateInfoNVの高レベルラッパー。

拡張: VK*NV*dedicated_allocation

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDedicatedAllocationMemoryAllocateInfoNV.html)

```julia
struct DedicatedAllocationMemoryAllocateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `image::Union{Ptr{Nothing}, Vulkan.Image}`
  * `buffer::Union{Ptr{Nothing}, Vulkan.Buffer}`
