引数:

  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::InstanceCreateFlag`: デフォルトは `0`
  * `application_info::ApplicationInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkInstanceCreateInfo.html)

```julia
InstanceCreateInfo(
    enabled_layer_names::AbstractArray,
    enabled_extension_names::AbstractArray;
    next,
    flags,
    application_info
) -> Vulkan.InstanceCreateInfo

```
