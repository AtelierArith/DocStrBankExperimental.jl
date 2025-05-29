Extension: VK_NV_shading_rate_image

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `sample_order_type::CoarseSampleOrderTypeNV`
  * `custom_sample_orders::Vector{_CoarseSampleOrderCustomNV}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetCoarseSampleOrderNV.html)

```julia
_cmd_set_coarse_sample_order_nv(
    command_buffer,
    sample_order_type::Vulkan.CoarseSampleOrderTypeNV,
    custom_sample_orders::AbstractArray
)

```
