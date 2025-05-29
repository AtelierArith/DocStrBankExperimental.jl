拡張: VK*EXT*validation_features

引数:

  * `enabled_validation_features::Vector{ValidationFeatureEnableEXT}`
  * `disabled_validation_features::Vector{ValidationFeatureDisableEXT}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationFeaturesEXT.html)

```julia
ValidationFeaturesEXT(
    enabled_validation_features::AbstractArray,
    disabled_validation_features::AbstractArray;
    next
) -> Vulkan.ValidationFeaturesEXT

```
