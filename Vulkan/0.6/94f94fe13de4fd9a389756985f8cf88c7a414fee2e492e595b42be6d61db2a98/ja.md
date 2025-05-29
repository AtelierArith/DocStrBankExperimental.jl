拡張: VK*NV*fragment*shading*rate_enums

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `shading_rate::FragmentShadingRateNV`
  * `combiner_ops::NTuple{2, FragmentShadingRateCombinerOpKHR}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetFragmentShadingRateEnumNV.html)

```julia
cmd_set_fragment_shading_rate_enum_nv(
    command_buffer,
    shading_rate::Vulkan.FragmentShadingRateNV,
    combiner_ops::Tuple{Vulkan.FragmentShadingRateCombinerOpKHR, Vulkan.FragmentShadingRateCombinerOpKHR}
)

```
