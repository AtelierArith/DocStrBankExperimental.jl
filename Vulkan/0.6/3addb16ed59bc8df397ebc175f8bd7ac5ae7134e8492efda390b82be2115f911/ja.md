VkPresentTimesInfoGOOGLEの高レベルラッパー。

拡張: VK*GOOGLE*display_timing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentTimesInfoGOOGLE.html)

```julia
struct PresentTimesInfoGOOGLE <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `times::Union{Ptr{Nothing}, Vector{Vulkan.PresentTimeGOOGLE}}`
