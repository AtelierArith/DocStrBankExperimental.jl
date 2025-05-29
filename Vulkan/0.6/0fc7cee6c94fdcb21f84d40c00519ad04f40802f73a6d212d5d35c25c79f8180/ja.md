拡張: VK*NV*present_barrier

引数:

  * `present_barrier_supported::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilitiesPresentBarrierNV.html)

```julia
_SurfaceCapabilitiesPresentBarrierNV(
    present_barrier_supported::Bool;
    next
) -> Vulkan._SurfaceCapabilitiesPresentBarrierNV

```
