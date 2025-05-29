拡張: VK*KHR*fragment*shading*rate

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `fragment_size::Extent2D`
  * `combiner_ops::NTuple{2, FragmentShadingRateCombinerOpKHR}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetFragmentShadingRateKHR.html)

```julia
cmd_set_fragment_shading_rate_khr(
    command_buffer,
    fragment_size::Vulkan.Extent2D,
    combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR}
)

```
