拡張: VK*NV*inherited*viewport*scissor

引数:

  * `viewport_scissor_2_d::Bool`
  * `viewport_depth_count::UInt32`
  * `viewport_depths::Viewport`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceViewportScissorInfoNV.html)

```julia
CommandBufferInheritanceViewportScissorInfoNV(
    viewport_scissor_2_d::Bool,
    viewport_depth_count::Integer,
    viewport_depths::Vulkan.Viewport;
    next
) -> Vulkan.CommandBufferInheritanceViewportScissorInfoNV

```
