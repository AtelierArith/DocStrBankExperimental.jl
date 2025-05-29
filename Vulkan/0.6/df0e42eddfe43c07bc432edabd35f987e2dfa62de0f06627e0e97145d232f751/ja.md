引数:

  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::InstanceCreateFlag`: デフォルトは `0`
  * `application_info::ApplicationInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateInstance.html)

```julia
Instance(
    enabled_layer_names::AbstractArray,
    enabled_extension_names::AbstractArray;
    allocator,
    next,
    flags,
    application_info
) -> Vulkan.Instance

```
