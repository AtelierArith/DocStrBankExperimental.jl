Extension: VK_EXT_sample_locations

Arguments:

  * `physical_device::PhysicalDevice`
  * `samples::SampleCountFlag`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceMultisamplePropertiesEXT.html)

```julia
get_physical_device_multisample_properties_ext(
    physical_device,
    samples::Vulkan.SampleCountFlag
) -> Vulkan.MultisamplePropertiesEXT

```
