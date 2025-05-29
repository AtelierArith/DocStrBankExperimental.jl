Extension: VK_HUAWEI_invocation_mask

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `image_layout::ImageLayout`
  * `image_view::ImageView`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBindInvocationMaskHUAWEI.html)

```julia
_cmd_bind_invocation_mask_huawei(
    command_buffer,
    image_layout::Vulkan.ImageLayout;
    image_view
)

```
