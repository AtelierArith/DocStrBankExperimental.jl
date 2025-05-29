Extension: VK_GOOGLE_display_timing

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `times::Vector{_PresentTimeGOOGLE}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentTimesInfoGOOGLE.html)

```julia
_PresentTimesInfoGOOGLE(
;
    next,
    times
) -> Vulkan._PresentTimesInfoGOOGLE

```
