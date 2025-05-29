拡張: VK*EXT*sample_locations

引数:

  * `sample_locations_enable::Bool`
  * `sample_locations_info::SampleLocationsInfoEXT`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineSampleLocationsStateCreateInfoEXT.html)

```julia
PipelineSampleLocationsStateCreateInfoEXT(
    sample_locations_enable::Bool,
    sample_locations_info::Vulkan.SampleLocationsInfoEXT;
    next
) -> Vulkan.PipelineSampleLocationsStateCreateInfoEXT

```
