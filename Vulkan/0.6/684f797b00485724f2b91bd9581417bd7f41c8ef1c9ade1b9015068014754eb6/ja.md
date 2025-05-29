引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `face_mask::StencilFaceFlag`
  * `fail_op::StencilOp`
  * `pass_op::StencilOp`
  * `depth_fail_op::StencilOp`
  * `compare_op::CompareOp`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetStencilOp.html)

```julia
_cmd_set_stencil_op(
    command_buffer,
    face_mask::Vulkan.StencilFaceFlag,
    fail_op::Vulkan.StencilOp,
    pass_op::Vulkan.StencilOp,
    depth_fail_op::Vulkan.StencilOp,
    compare_op::Vulkan.CompareOp
)

```
