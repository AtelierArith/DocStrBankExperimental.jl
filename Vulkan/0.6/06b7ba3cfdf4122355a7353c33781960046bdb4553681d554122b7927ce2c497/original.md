Arguments:

  * `device::Device`
  * `create_info::DescriptorSetLayoutCreateInfo`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDescriptorSetLayoutSupport.html)

```julia
get_descriptor_set_layout_support(
    device,
    create_info::Vulkan.DescriptorSetLayoutCreateInfo,
    next_types::Type...
) -> Vulkan.DescriptorSetLayoutSupport

```
