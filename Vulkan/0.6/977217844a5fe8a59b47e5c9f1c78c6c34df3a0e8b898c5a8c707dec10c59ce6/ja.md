引数:

  * `name::String`
  * `version::String`
  * `purposes::ToolPurposeFlag`
  * `description::String`
  * `layer::String`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceToolProperties.html)

```julia
_PhysicalDeviceToolProperties(
    name::AbstractString,
    version::AbstractString,
    purposes::Vulkan.ToolPurposeFlag,
    description::AbstractString,
    layer::AbstractString;
    next
)

```
