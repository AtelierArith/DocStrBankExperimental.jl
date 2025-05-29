VkMemoryRequirementsの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryRequirements.html)

```julia
struct MemoryRequirements <: Vulkan.HighLevelStruct
```

  * `size::UInt64`
  * `alignment::UInt64`
  * `memory_type_bits::UInt32`
