Arguments:

  * `fail_op::StencilOp`
  * `pass_op::StencilOp`
  * `depth_fail_op::StencilOp`
  * `compare_op::CompareOp`
  * `compare_mask::UInt32`
  * `write_mask::UInt32`
  * `reference::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkStencilOpState.html)

```julia
_StencilOpState(
    fail_op::Vulkan.StencilOp,
    pass_op::Vulkan.StencilOp,
    depth_fail_op::Vulkan.StencilOp,
    compare_op::Vulkan.CompareOp,
    compare_mask::Integer,
    write_mask::Integer,
    reference::Integer
) -> Vulkan._StencilOpState

```
