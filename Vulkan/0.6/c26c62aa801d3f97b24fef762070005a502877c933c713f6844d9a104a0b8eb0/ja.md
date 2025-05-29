引数:

  * `patch_control_points::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineTessellationStateCreateInfo.html)

```julia
_PipelineTessellationStateCreateInfo(
    patch_control_points::Integer;
    next,
    flags
) -> Vulkan._PipelineTessellationStateCreateInfo

```
