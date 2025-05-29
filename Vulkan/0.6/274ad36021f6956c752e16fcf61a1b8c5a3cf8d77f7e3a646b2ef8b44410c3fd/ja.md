戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkEnumerateInstanceLayerProperties.html)

```julia
_enumerate_instance_layer_properties(

) -> ResultTypes.Result{Vector{Vulkan._LayerProperties}, Vulkan.VulkanError}

```
