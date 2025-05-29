Arguments:

  * `create_info::_ImageCreateInfo`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `plane_aspect::ImageAspectFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceImageMemoryRequirements.html)

```julia
_DeviceImageMemoryRequirements(
    create_info::Vulkan._ImageCreateInfo;
    next,
    plane_aspect
)

```
