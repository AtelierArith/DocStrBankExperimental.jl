VkPipelineCoverageToColorStateCreateInfoNVの高レベルラッパー。

拡張: VK*NV*fragment*coverage*to_color

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCoverageToColorStateCreateInfoNV.html)

```julia
struct PipelineCoverageToColorStateCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `coverage_to_color_enable::Bool`
  * `coverage_to_color_location::UInt32`
