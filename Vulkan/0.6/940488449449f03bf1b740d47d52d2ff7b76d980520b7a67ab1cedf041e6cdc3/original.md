Extension: VK_NV_shading_rate_image

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `sample_order_type::CoarseSampleOrderTypeNV`
  * `custom_sample_orders::Vector{CoarseSampleOrderCustomNV}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetCoarseSampleOrderNV.html)

```julia
cmd_set_coarse_sample_order_nv(
    command_buffer,
    sample_order_type::Vulkan.CoarseSampleOrderTypeNV,
    custom_sample_orders::AbstractArray
)

```
