Arguments:

  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::InstanceCreateFlag`: defaults to `0`
  * `application_info::_ApplicationInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkInstanceCreateInfo.html)

```julia
_InstanceCreateInfo(
    enabled_layer_names::AbstractArray,
    enabled_extension_names::AbstractArray;
    next,
    flags,
    application_info
) -> Vulkan._InstanceCreateInfo

```
