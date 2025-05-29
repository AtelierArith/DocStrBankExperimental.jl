Arguments:

  * `name::String`
  * `version::String`
  * `purposes::ToolPurposeFlag`
  * `description::String`
  * `layer::String`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceToolProperties.html)

```julia
PhysicalDeviceToolProperties(
    name::AbstractString,
    version::AbstractString,
    purposes::Vulkan.ToolPurposeFlag,
    description::AbstractString,
    layer::AbstractString;
    next
) -> Vulkan.PhysicalDeviceToolProperties

```
