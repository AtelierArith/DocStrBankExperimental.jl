拡張: VK*KHR*fragment*shading*rate

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `fragment_size::_Extent2D`
  * `combiner_ops::NTuple{2, FragmentShadingRateCombinerOpKHR}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetFragmentShadingRateKHR.html)

```julia
_cmd_set_fragment_shading_rate_khr(
    command_buffer,
    fragment_size::Vulkan._Extent2D,
    combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR}
)

```
