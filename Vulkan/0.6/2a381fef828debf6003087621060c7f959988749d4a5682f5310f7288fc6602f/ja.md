拡張: VK*KHR*surface*protected*capabilities

引数:

  * `supports_protected::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceProtectedCapabilitiesKHR.html)

```julia
_SurfaceProtectedCapabilitiesKHR(
    supports_protected::Bool;
    next
) -> Vulkan._SurfaceProtectedCapabilitiesKHR

```
