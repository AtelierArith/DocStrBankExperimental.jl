引数:

  * `patch_control_points::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineTessellationStateCreateInfo.html)

```julia
PipelineTessellationStateCreateInfo(
    patch_control_points::Integer;
    next,
    flags
) -> Vulkan.PipelineTessellationStateCreateInfo

```
