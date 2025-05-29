VkShaderModuleCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderModuleCreateInfo.html)

```julia
struct ShaderModuleCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `code_size::UInt64`
  * `code::Vector{UInt32}`
