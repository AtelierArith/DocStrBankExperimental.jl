Extension: VK_AMD_device_coherent_memory

Arguments:

  * `device_coherent_memory::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceCoherentMemoryFeaturesAMD.html)

```julia
_PhysicalDeviceCoherentMemoryFeaturesAMD(
    device_coherent_memory::Bool;
    next
) -> Vulkan._PhysicalDeviceCoherentMemoryFeaturesAMD

```
