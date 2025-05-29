拡張: VK*AMD*device*coherent*memory

引数:

  * `device_coherent_memory::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceCoherentMemoryFeaturesAMD.html)

```julia
_PhysicalDeviceCoherentMemoryFeaturesAMD(
    device_coherent_memory::Bool;
    next
) -> Vulkan._PhysicalDeviceCoherentMemoryFeaturesAMD

```
