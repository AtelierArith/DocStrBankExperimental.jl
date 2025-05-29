Arguments:

  * `physical_device::PhysicalDevice`
  * `format::Format`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceFormatProperties2.html)

```julia
_get_physical_device_format_properties_2(
    physical_device,
    format::Vulkan.Format,
    next_types::Type...
) -> Vulkan._FormatProperties2

```
