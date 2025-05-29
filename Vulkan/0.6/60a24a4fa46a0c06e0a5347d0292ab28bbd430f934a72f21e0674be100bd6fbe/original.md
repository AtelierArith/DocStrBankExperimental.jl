Extension: VK_EXT_opacity_micromap

Arguments:

  * `device::Device`
  * `build_type::AccelerationStructureBuildTypeKHR`
  * `build_info::MicromapBuildInfoEXT`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetMicromapBuildSizesEXT.html)

```julia
get_micromap_build_sizes_ext(
    device,
    build_type::Vulkan.AccelerationStructureBuildTypeKHR,
    build_info::Vulkan.MicromapBuildInfoEXT
) -> Vulkan.MicromapBuildSizesInfoEXT

```
