Extension: VK_KHR_fragment_shading_rate

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `fragment_size::Extent2D`
  * `combiner_ops::NTuple{2, FragmentShadingRateCombinerOpKHR}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetFragmentShadingRateKHR.html)

```julia
cmd_set_fragment_shading_rate_khr(
    command_buffer,
    fragment_size::Vulkan.Extent2D,
    combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR}
)

```
