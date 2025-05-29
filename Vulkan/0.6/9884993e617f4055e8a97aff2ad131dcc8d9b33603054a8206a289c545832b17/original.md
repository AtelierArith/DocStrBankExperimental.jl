Arguments:

  * `plane_aspect::ImageAspectFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImagePlaneMemoryInfo.html)

```julia
_BindImagePlaneMemoryInfo(
    plane_aspect::Vulkan.ImageAspectFlag;
    next
) -> Vulkan._BindImagePlaneMemoryInfo

```
