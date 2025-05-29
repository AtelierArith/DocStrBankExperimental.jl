VkMicromapBuildSizesInfoEXTの高レベルラッパー。

拡張: VK*EXT*opacity_micromap

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapBuildSizesInfoEXT.html)

```julia
struct MicromapBuildSizesInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `micromap_size::UInt64`
  * `build_scratch_size::UInt64`
  * `discardable::Bool`
