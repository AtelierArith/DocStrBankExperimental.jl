VkPresentIdKHRの高レベルラッパー。

拡張: VK*KHR*present_id

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentIdKHR.html)

```julia
struct PresentIdKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `present_ids::Union{Ptr{Nothing}, Vector{UInt64}}`
