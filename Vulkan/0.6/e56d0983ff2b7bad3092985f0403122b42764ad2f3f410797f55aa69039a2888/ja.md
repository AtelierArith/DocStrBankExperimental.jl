VkPresentRegionKHRの高レベルラッパー。

拡張: VK*KHR*incremental_present

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentRegionKHR.html)

```julia
struct PresentRegionKHR <: Vulkan.HighLevelStruct
```

  * `rectangles::Union{Ptr{Nothing}, Vector{Vulkan.RectLayerKHR}}`
