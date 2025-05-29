Extension: VK_NV_present_barrier

Arguments:

  * `present_barrier_supported::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilitiesPresentBarrierNV.html)

```julia
_SurfaceCapabilitiesPresentBarrierNV(
    present_barrier_supported::Bool;
    next
) -> Vulkan._SurfaceCapabilitiesPresentBarrierNV

```
