拡張: VK*NV*copy*memory*indirect

引数:

  * `indirect_copy::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceCopyMemoryIndirectFeaturesNV.html)

```julia
_PhysicalDeviceCopyMemoryIndirectFeaturesNV(
    indirect_copy::Bool;
    next
) -> Vulkan._PhysicalDeviceCopyMemoryIndirectFeaturesNV

```
