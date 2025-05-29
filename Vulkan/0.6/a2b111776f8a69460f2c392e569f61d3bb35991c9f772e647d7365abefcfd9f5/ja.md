拡張: VK*EXT*pipeline_properties

引数:

  * `pipeline_identifier::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelinePropertiesIdentifierEXT.html)

```julia
PipelinePropertiesIdentifierEXT(
    pipeline_identifier::NTuple{16, UInt8};
    next
) -> Vulkan.PipelinePropertiesIdentifierEXT

```
