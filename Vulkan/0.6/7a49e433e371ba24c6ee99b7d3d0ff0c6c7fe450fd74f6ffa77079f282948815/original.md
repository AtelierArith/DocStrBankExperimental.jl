Arguments:

  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::InstanceCreateFlag`: defaults to `0`
  * `application_info::ApplicationInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkInstanceCreateInfo.html)

```julia
InstanceCreateInfo(
    enabled_layer_names::AbstractArray,
    enabled_extension_names::AbstractArray;
    next,
    flags,
    application_info
) -> Vulkan.InstanceCreateInfo

```
