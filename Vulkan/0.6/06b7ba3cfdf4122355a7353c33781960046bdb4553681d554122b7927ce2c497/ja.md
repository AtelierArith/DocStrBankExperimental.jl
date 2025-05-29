引数:

  * `device::Device`
  * `create_info::DescriptorSetLayoutCreateInfo`
  * `next_types::Type...`: `next` チェーンの一部として初期化し含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDescriptorSetLayoutSupport.html)

```julia
get_descriptor_set_layout_support(
    device,
    create_info::Vulkan.DescriptorSetLayoutCreateInfo,
    next_types::Type...
) -> Vulkan.DescriptorSetLayoutSupport

```
