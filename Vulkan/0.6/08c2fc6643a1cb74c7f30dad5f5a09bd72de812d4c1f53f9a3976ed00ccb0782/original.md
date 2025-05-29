High-level wrapper for VkValidationFeaturesEXT.

Extension: VK_EXT_validation_features

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationFeaturesEXT.html)

```julia
struct ValidationFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `enabled_validation_features::Vector{Vulkan.ValidationFeatureEnableEXT}`
  * `disabled_validation_features::Vector{Vulkan.ValidationFeatureDisableEXT}`
