VkClearRectの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkClearRect.html)

```julia
struct ClearRect <: Vulkan.HighLevelStruct
```

  * `rect::Vulkan.Rect2D`
  * `base_array_layer::UInt32`
  * `layer_count::UInt32`
