引数:

  * `create_info::_ImageCreateInfo`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `plane_aspect::ImageAspectFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceImageMemoryRequirements.html)

```julia
_DeviceImageMemoryRequirements(
    create_info::Vulkan._ImageCreateInfo;
    next,
    plane_aspect
)

```
