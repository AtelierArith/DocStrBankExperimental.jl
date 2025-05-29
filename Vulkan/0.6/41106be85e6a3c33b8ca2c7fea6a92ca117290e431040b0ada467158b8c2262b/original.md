Arguments:

  * `create_info::ImageCreateInfo`
  * `next::Any`: defaults to `C_NULL`
  * `plane_aspect::ImageAspectFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceImageMemoryRequirements.html)

```julia
DeviceImageMemoryRequirements(
    create_info::Vulkan.ImageCreateInfo;
    next,
    plane_aspect
) -> Vulkan.DeviceImageMemoryRequirements

```
