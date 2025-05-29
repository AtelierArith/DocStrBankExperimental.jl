VkFormatProperties3の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFormatProperties3.html)

```julia
struct FormatProperties3 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `linear_tiling_features::UInt64`
  * `optimal_tiling_features::UInt64`
  * `buffer_features::UInt64`
