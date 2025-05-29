VkGraphicsPipelineShaderGroupsCreateInfoNVの高レベルラッパー。

拡張: VK*NV*device*generated*commands

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineShaderGroupsCreateInfoNV.html)

```julia
struct GraphicsPipelineShaderGroupsCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `groups::Vector{Vulkan.GraphicsShaderGroupCreateInfoNV}`
  * `pipelines::Vector{Vulkan.Pipeline}`
