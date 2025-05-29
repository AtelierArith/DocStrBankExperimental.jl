引数:

  * `device::Device`
  * `descriptor_pool::DescriptorPool` (externsync)
  * `descriptor_sets::Vector{DescriptorSet}` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkFreeDescriptorSets.html)

```julia
_free_descriptor_sets(
    device,
    descriptor_pool,
    descriptor_sets::AbstractArray
)

```
