Extension: VK_KHR_display

Arguments:

  * `display::DisplayKHR`
  * `display_name::String`
  * `physical_dimensions::_Extent2D`
  * `physical_resolution::_Extent2D`
  * `plane_reorder_possible::Bool`
  * `persistent_content::Bool`
  * `supported_transforms::SurfaceTransformFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPropertiesKHR.html)

```julia
_DisplayPropertiesKHR(
    display,
    display_name::AbstractString,
    physical_dimensions::Vulkan._Extent2D,
    physical_resolution::Vulkan._Extent2D,
    plane_reorder_possible::Bool,
    persistent_content::Bool;
    supported_transforms
) -> Vulkan._DisplayPropertiesKHR

```
