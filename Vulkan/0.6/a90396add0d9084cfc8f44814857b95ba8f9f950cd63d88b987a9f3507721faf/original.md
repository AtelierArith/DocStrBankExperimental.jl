Extension: VK_EXT_pipeline_properties

Arguments:

  * `pipeline_properties_identifier::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePipelinePropertiesFeaturesEXT.html)

```julia
_PhysicalDevicePipelinePropertiesFeaturesEXT(
    pipeline_properties_identifier::Bool;
    next
) -> Vulkan._PhysicalDevicePipelinePropertiesFeaturesEXT

```
