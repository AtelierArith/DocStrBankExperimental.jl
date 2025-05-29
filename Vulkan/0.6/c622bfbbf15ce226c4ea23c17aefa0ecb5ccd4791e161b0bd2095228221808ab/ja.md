VkSurfacePresentModeCompatibilityEXTの高レベルラッパー。

拡張: VK*EXT*surface_maintenance1

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfacePresentModeCompatibilityEXT.html)

```julia
struct SurfacePresentModeCompatibilityEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `present_modes::Union{Ptr{Nothing}, Vector{Vulkan.PresentModeKHR}}`
