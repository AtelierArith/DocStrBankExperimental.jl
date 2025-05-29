Extension: VK_EXT_pipeline_properties

Arguments:

  * `pipeline_identifier::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelinePropertiesIdentifierEXT.html)

```julia
PipelinePropertiesIdentifierEXT(
    pipeline_identifier::NTuple{16, UInt8};
    next
) -> Vulkan.PipelinePropertiesIdentifierEXT

```
