Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_LAYER_NOT_PRESENT`

Arguments:

  * `layer_name::String`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkEnumerateInstanceExtensionProperties.html)

```julia
_enumerate_instance_extension_properties(
;
    layer_name
) -> ResultTypes.Result{Vector{Vulkan._ExtensionProperties}, Vulkan.VulkanError}

```
