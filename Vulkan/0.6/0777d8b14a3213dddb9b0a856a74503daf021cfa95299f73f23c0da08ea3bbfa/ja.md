VkCommandBufferInheritanceViewportScissorInfoNVの高レベルラッパー。

拡張: VK*NV*inherited*viewport*scissor

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceViewportScissorInfoNV.html)

```julia
struct CommandBufferInheritanceViewportScissorInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `viewport_scissor_2_d::Bool`
  * `viewport_depth_count::UInt32`
  * `viewport_depths::Vulkan.Viewport`
