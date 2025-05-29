VkPipelineShaderStageModuleIdentifierCreateInfoEXTの高レベルラッパー。

拡張: VK*EXT*shader*module*identifier

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineShaderStageModuleIdentifierCreateInfoEXT.html)

```julia
struct PipelineShaderStageModuleIdentifierCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `identifier_size::UInt32`
  * `identifier::Vector{UInt8}`
