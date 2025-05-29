VkStencilOpStateの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkStencilOpState.html)

```julia
struct StencilOpState <: Vulkan.HighLevelStruct
```

  * `fail_op::Vulkan.StencilOp`
  * `pass_op::Vulkan.StencilOp`
  * `depth_fail_op::Vulkan.StencilOp`
  * `compare_op::Vulkan.CompareOp`
  * `compare_mask::UInt32`
  * `write_mask::UInt32`
  * `reference::UInt32`
