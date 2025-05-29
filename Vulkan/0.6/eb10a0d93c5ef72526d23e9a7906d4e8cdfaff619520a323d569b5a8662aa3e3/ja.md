拡張: VK*KHR*get*display*properties2

引数:

  * `mode::DisplayModeKHR` (externsync)
  * `plane_index::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneInfo2KHR.html)

```julia
_DisplayPlaneInfo2KHR(
    mode,
    plane_index::Integer;
    next
) -> Vulkan._DisplayPlaneInfo2KHR

```
