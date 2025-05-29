拡張: VK*NV*fragment*coverage*to_color

引数:

  * `coverage_to_color_enable::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `coverage_to_color_location::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCoverageToColorStateCreateInfoNV.html)

```julia
_PipelineCoverageToColorStateCreateInfoNV(
    coverage_to_color_enable::Bool;
    next,
    flags,
    coverage_to_color_location
) -> Vulkan._PipelineCoverageToColorStateCreateInfoNV

```
