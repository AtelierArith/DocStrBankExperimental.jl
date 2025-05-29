拡張: VK*KHR*get*display*properties2

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceDisplayProperties2KHR.html)

```julia
get_physical_device_display_properties_2_khr(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.DisplayProperties2KHR}, Vulkan.VulkanError}

```
