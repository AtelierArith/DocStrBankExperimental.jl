Extension: VK_EXT_sample_locations

Arguments:

  * `sample_locations_enable::Bool`
  * `sample_locations_info::_SampleLocationsInfoEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineSampleLocationsStateCreateInfoEXT.html)

```julia
_PipelineSampleLocationsStateCreateInfoEXT(
    sample_locations_enable::Bool,
    sample_locations_info::Vulkan._SampleLocationsInfoEXT;
    next
) -> Vulkan._PipelineSampleLocationsStateCreateInfoEXT

```
