Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_LAYER_NOT_PRESENT`
  * `ERROR_EXTENSION_NOT_PRESENT`
  * `ERROR_INCOMPATIBLE_DRIVER`

Arguments:

  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::InstanceCreateFlag`: defaults to `0`
  * `application_info::ApplicationInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateInstance.html)

```julia
create_instance(
    enabled_layer_names::AbstractArray,
    enabled_extension_names::AbstractArray;
    allocator,
    next,
    flags,
    application_info
) -> ResultTypes.Result{Vulkan.Instance, Vulkan.VulkanError}

```
