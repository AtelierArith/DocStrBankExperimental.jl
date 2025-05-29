VkValidationFlagsEXTの高レベルラッパー。

拡張: VK*EXT*validation_flags

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkValidationFlagsEXT.html)

```julia
struct ValidationFlagsEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `disabled_validation_checks::Vector{Vulkan.ValidationCheckEXT}`
