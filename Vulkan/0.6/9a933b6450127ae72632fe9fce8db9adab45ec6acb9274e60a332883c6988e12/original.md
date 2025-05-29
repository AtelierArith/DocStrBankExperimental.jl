Extension: VK_QCOM_rotated_copy_commands

Arguments:

  * `transform::SurfaceTransformFlagKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyCommandTransformInfoQCOM.html)

```julia
_CopyCommandTransformInfoQCOM(
    transform::Vulkan.SurfaceTransformFlagKHR;
    next
) -> Vulkan._CopyCommandTransformInfoQCOM

```
