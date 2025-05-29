VkSubresourceLayoutの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubresourceLayout.html)

```julia
struct SubresourceLayout <: Vulkan.HighLevelStruct
```

  * `offset::UInt64`
  * `size::UInt64`
  * `row_pitch::UInt64`
  * `array_pitch::UInt64`
  * `depth_pitch::UInt64`
