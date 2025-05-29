VkSpecializationInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSpecializationInfo.html)

```julia
struct SpecializationInfo <: Vulkan.HighLevelStruct
```

  * `map_entries::Vector{Vulkan.SpecializationMapEntry}`
  * `data_size::Union{Ptr{Nothing}, UInt64}`
  * `data::Ptr{Nothing}`
