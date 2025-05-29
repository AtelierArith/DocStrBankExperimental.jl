Extension: VK_EXT_validation_features

Arguments:

  * `enabled_validation_features::Vector{ValidationFeatureEnableEXT}`
  * `disabled_validation_features::Vector{ValidationFeatureDisableEXT}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationFeaturesEXT.html)

```julia
ValidationFeaturesEXT(
    enabled_validation_features::AbstractArray,
    disabled_validation_features::AbstractArray;
    next
) -> Vulkan.ValidationFeaturesEXT

```
