戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_LAYER_NOT_PRESENT`
  * `ERROR_EXTENSION_NOT_PRESENT`
  * `ERROR_INCOMPATIBLE_DRIVER`

引数:

  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::InstanceCreateFlag`: デフォルトは `0`
  * `application_info::ApplicationInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateInstance.html)

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
