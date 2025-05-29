引数:

  * `device::Device`
  * `descriptor_writes::Vector{WriteDescriptorSet}`
  * `descriptor_copies::Vector{CopyDescriptorSet}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkUpdateDescriptorSets.html)

```julia
update_descriptor_sets(
    device,
    descriptor_writes::AbstractArray,
    descriptor_copies::AbstractArray
)

```
