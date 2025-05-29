Arguments:

  * `patch_control_points::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineTessellationStateCreateInfo.html)

```julia
_PipelineTessellationStateCreateInfo(
    patch_control_points::Integer;
    next,
    flags
) -> Vulkan._PipelineTessellationStateCreateInfo

```
