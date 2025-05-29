VkAccelerationStructureMemoryRequirementsInfoNVの高レベルラッパー。

拡張: VK*NV*ray_tracing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMemoryRequirementsInfoNV.html)

```julia
struct AccelerationStructureMemoryRequirementsInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::Vulkan.AccelerationStructureMemoryRequirementsTypeNV`
  * `acceleration_structure::Vulkan.AccelerationStructureNV`
