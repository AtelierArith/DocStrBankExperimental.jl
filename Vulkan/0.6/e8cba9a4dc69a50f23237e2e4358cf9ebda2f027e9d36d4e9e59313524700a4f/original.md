Extension: VK_NV_inherited_viewport_scissor

Arguments:

  * `viewport_scissor_2_d::Bool`
  * `viewport_depth_count::UInt32`
  * `viewport_depths::_Viewport`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceViewportScissorInfoNV.html)

```julia
_CommandBufferInheritanceViewportScissorInfoNV(
    viewport_scissor_2_d::Bool,
    viewport_depth_count::Integer,
    viewport_depths::Vulkan._Viewport;
    next
) -> Vulkan._CommandBufferInheritanceViewportScissorInfoNV

```
