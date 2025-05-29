Extension: VK_KHR_display

Arguments:

  * `display::DisplayKHR`
  * `display_name::String`
  * `physical_dimensions::Extent2D`
  * `physical_resolution::Extent2D`
  * `plane_reorder_possible::Bool`
  * `persistent_content::Bool`
  * `supported_transforms::SurfaceTransformFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPropertiesKHR.html)

```julia
DisplayPropertiesKHR(
    display::Vulkan.DisplayKHR,
    display_name::AbstractString,
    physical_dimensions::Vulkan.Extent2D,
    physical_resolution::Vulkan.Extent2D,
    plane_reorder_possible::Bool,
    persistent_content::Bool;
    supported_transforms
) -> Vulkan.DisplayPropertiesKHR

```
