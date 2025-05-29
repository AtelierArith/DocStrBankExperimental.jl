Extension: VK_NV_fragment_coverage_to_color

Arguments:

  * `coverage_to_color_enable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `coverage_to_color_location::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCoverageToColorStateCreateInfoNV.html)

```julia
_PipelineCoverageToColorStateCreateInfoNV(
    coverage_to_color_enable::Bool;
    next,
    flags,
    coverage_to_color_location
) -> Vulkan._PipelineCoverageToColorStateCreateInfoNV

```
