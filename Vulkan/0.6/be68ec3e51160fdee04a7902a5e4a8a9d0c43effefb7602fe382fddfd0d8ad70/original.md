Extension: VK_EXT_image_2d_view_of_3d

Arguments:

  * `image_2_d_view_of_3_d::Bool`
  * `sampler_2_d_view_of_3_d::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImage2DViewOf3DFeaturesEXT.html)

```julia
_PhysicalDeviceImage2DViewOf3DFeaturesEXT(
    image_2_d_view_of_3_d::Bool,
    sampler_2_d_view_of_3_d::Bool;
    next
) -> Vulkan._PhysicalDeviceImage2DViewOf3DFeaturesEXT

```
