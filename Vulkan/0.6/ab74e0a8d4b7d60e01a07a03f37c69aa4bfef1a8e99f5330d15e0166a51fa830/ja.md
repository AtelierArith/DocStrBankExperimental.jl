VkDescriptorImageInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorImageInfo.html)

```julia
struct DescriptorImageInfo <: Vulkan.HighLevelStruct
```

  * `sampler::Vulkan.Sampler`
  * `image_view::Vulkan.ImageView`
  * `image_layout::Vulkan.ImageLayout`
