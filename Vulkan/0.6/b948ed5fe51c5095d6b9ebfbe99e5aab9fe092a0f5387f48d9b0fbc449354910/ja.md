拡張: VK*NV*present_barrier

引数:

  * `present_barrier::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePresentBarrierFeaturesNV.html)

```julia
_PhysicalDevicePresentBarrierFeaturesNV(
    present_barrier::Bool;
    next
) -> Vulkan._PhysicalDevicePresentBarrierFeaturesNV

```
