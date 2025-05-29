VkSamplerCustomBorderColorCreateInfoEXTの高レベルラッパー。

拡張: VK*EXT*custom*border*color

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerCustomBorderColorCreateInfoEXT.html)

```julia
struct SamplerCustomBorderColorCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `custom_border_color::Vulkan.ClearColorValue`
  * `format::Vulkan.Format`
