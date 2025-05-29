VkShaderModuleIdentifierEXTの高レベルラッパー。

拡張: VK*EXT*shader*module*identifier

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderModuleIdentifierEXT.html)

```julia
struct ShaderModuleIdentifierEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `identifier_size::UInt32`
  * `identifier::NTuple{32, UInt8}`
