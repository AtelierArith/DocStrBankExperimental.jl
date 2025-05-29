拡張: VK*EXT*sample_locations

引数:

  * `sample_locations_enable::Bool`
  * `sample_locations_info::_SampleLocationsInfoEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineSampleLocationsStateCreateInfoEXT.html)

```julia
_PipelineSampleLocationsStateCreateInfoEXT(
    sample_locations_enable::Bool,
    sample_locations_info::Vulkan._SampleLocationsInfoEXT;
    next
) -> Vulkan._PipelineSampleLocationsStateCreateInfoEXT

```
