High-level wrapper for VkPresentTimesInfoGOOGLE.

Extension: VK_GOOGLE_display_timing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentTimesInfoGOOGLE.html)

```julia
struct PresentTimesInfoGOOGLE <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `times::Union{Ptr{Nothing}, Vector{Vulkan.PresentTimeGOOGLE}}`
