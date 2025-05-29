VkValidationFeaturesEXTの高レベルラッパー。

拡張: VK*EXT*validation_features

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationFeaturesEXT.html)

```julia
struct ValidationFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `enabled_validation_features::Vector{Vulkan.ValidationFeatureEnableEXT}`
  * `disabled_validation_features::Vector{Vulkan.ValidationFeatureDisableEXT}`
