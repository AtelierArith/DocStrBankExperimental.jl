VkPresentRegionsKHRの高レベルラッパー。

拡張: VK*KHR*incremental_present

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentRegionsKHR.html)

```julia
struct PresentRegionsKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `regions::Union{Ptr{Nothing}, Vector{Vulkan.PresentRegionKHR}}`
