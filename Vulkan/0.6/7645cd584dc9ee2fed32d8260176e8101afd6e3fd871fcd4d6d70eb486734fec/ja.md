拡張: VK*NV*present_barrier

引数:

  * `present_barrier_supported::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilitiesPresentBarrierNV.html)

```julia
SurfaceCapabilitiesPresentBarrierNV(
    present_barrier_supported::Bool;
    next
) -> Vulkan.SurfaceCapabilitiesPresentBarrierNV

```
