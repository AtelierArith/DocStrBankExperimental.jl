引数:

  * `create_info::ImageCreateInfo`
  * `next::Any`: デフォルトは `C_NULL`
  * `plane_aspect::ImageAspectFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceImageMemoryRequirements.html)

```julia
DeviceImageMemoryRequirements(
    create_info::Vulkan.ImageCreateInfo;
    next,
    plane_aspect
) -> Vulkan.DeviceImageMemoryRequirements

```
