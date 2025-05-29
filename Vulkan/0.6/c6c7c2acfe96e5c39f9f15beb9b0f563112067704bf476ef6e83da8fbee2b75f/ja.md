VkRectLayerKHRの高レベルラッパー。

拡張: VK*KHR*incremental_present

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRectLayerKHR.html)

```julia
struct RectLayerKHR <: Vulkan.HighLevelStruct
```

  * `offset::Vulkan.Offset2D`
  * `extent::Vulkan.Extent2D`
  * `layer::UInt32`
