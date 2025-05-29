VkImageMemoryBarrier2の中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageMemoryBarrier2.html)

```julia
struct _ImageMemoryBarrier2 <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkImageMemoryBarrier2`
  * `deps::Vector{Any}`
  * `image::Vulkan.Image`
