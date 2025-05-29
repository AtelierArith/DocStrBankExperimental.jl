Extension: VK_AMD_pipeline_compiler_control

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `compiler_control_flags::PipelineCompilerControlFlagAMD`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCompilerControlCreateInfoAMD.html)

```julia
_PipelineCompilerControlCreateInfoAMD(
;
    next,
    compiler_control_flags
) -> Vulkan._PipelineCompilerControlCreateInfoAMD

```
