VkDescriptorImageInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorImageInfo.html)

```julia
struct _DescriptorImageInfo <: Vulkan.VulkanStruct{false}
```

  * `vks::VulkanCore.LibVulkan.VkDescriptorImageInfo`
  * `sampler::Vulkan.Sampler`
  * `image_view::Vulkan.ImageView`
