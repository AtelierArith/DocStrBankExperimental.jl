Arguments:

  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::InstanceCreateFlag`: defaults to `0`
  * `application_info::ApplicationInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateInstance.html)

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
