拡張: VK*AMD*pipeline*compiler*control

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `compiler_control_flags::PipelineCompilerControlFlagAMD`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCompilerControlCreateInfoAMD.html)

```julia
_PipelineCompilerControlCreateInfoAMD(
;
    next,
    compiler_control_flags
) -> Vulkan._PipelineCompilerControlCreateInfoAMD

```
