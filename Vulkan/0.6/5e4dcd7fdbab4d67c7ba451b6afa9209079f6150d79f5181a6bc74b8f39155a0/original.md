Extension: VK_EXT_pipeline_protected_access

Arguments:

  * `pipeline_protected_access::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePipelineProtectedAccessFeaturesEXT.html)

```julia
_PhysicalDevicePipelineProtectedAccessFeaturesEXT(
    pipeline_protected_access::Bool;
    next
) -> Vulkan._PhysicalDevicePipelineProtectedAccessFeaturesEXT

```
