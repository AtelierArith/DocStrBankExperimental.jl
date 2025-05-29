VkAccelerationStructureCreateInfoNVの高レベルラッパー。

拡張: VK*NV*ray_tracing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCreateInfoNV.html)

```julia
struct AccelerationStructureCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `compacted_size::UInt64`
  * `info::Vulkan.AccelerationStructureInfoNV`
