引数:

  * `subgroup_size_control::Bool`
  * `compute_full_subgroups::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSubgroupSizeControlFeatures.html)

```julia
_PhysicalDeviceSubgroupSizeControlFeatures(
    subgroup_size_control::Bool,
    compute_full_subgroups::Bool;
    next
) -> Vulkan._PhysicalDeviceSubgroupSizeControlFeatures

```
